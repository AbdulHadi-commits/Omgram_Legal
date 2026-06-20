cd ~/orange_pi_deploy
source venv/bin/activate
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"
ls ~/orange_pi_deploy/recordings/car_photos/ | head -20
ls ~/orange_pi_deploy/recordings/car_photos/*.mp4
python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 3
for f in recordings/car_photos/*.mp4; do
  echo "Processing video: $f"
  python gate_sync.py --video "$f" --every 1 --max-frames 5 --preprocess none --delay 3
done




cd ~/orange_pi_deploy
cp gate_sync.py gate_sync.py.broken

python3 << 'ENDFIX'
from pathlib import Path
import py_compile

p = Path("gate_sync.py")
t = p.read_text()

start = t.find("def sync_video(")
end = t.find("\ndef sync_webcam(")
if start == -1 or end == -1:
    raise SystemExit("ERROR: could not find sync_video in file")

if "_event_dedup_key" not in t[:start]:
    helper = '''
def _event_dedup_key(result: PipelineResult) -> str | None:
    invalid_plates = {"", "NO_PLATE_DETECTED", "NO_CHARS", "NO_TEXT", "UNKNOWN"}
    for raw in result.plate_texts or []:
        plate = str(raw).strip().upper()
        if plate and plate not in invalid_plates:
            return f"plate:{plate}"
    label = (result.vehicle_label or "").strip().lower().replace(" ", "_")
    if label:
        return f"vehicle:{label}"
    return None


'''
    t = t.replace("def sync_image(", helper + "def sync_image(", 1)
    start = t.find("def sync_video(")
    end = t.find("\ndef sync_webcam(")

new_block = '''def sync_video(path: Path, models, args) -> None:
    cap = cv2.VideoCapture(str(path))
    if not cap.isOpened():
        print(f"Cannot open video: {path}")
        sys.exit(1)

    fps = cap.get(cv2.CAP_PROP_FPS) or 25.0
    frame_step = args.every_frames if args.every_frames > 0 else max(int(round(fps * args.every)), 1)

    print(f"Video: {path.name} - sample every {frame_step} frame(s), dedupe by plate per video\\n")
    frame_idx = 0
    posted = 0
    skipped = 0
    seen_keys: set[str] = set()

    while True:
        ret, frame = cap.read()
        if not ret:
            break
        if frame_idx % frame_step != 0:
            frame_idx += 1
            continue
        if args.max_frames > 0 and posted >= args.max_frames:
            break

        pil = Image.fromarray(cv2.cvtColor(frame, cv2.COLOR_BGR2RGB))
        print(f"Frame {frame_idx} ({frame_idx / fps:.1f}s)")
        result = process_pil_image(pil, models, preprocess_mode=args.preprocess)
        _print_result(result)

        dedup_key = _event_dedup_key(result)
        if dedup_key and dedup_key in seen_keys:
            skipped += 1
            print("  Website : skipped (duplicate - already uploaded for this video)\\n")
            frame_idx += 1
            continue

        try:
            site = post_to_vercel(args.api, args.gate_token, result, dry_run=args.dry_run)
            eid = site.get("event", {}).get("id")
            action = site.get("gate_action")
            print(f"  Website : event id {eid} -> {action}\\n")
            posted += 1
            if dedup_key:
                seen_keys.add(dedup_key)
        except Exception as err:
            print(f"  Website : FAILED ({err})\\n")

        frame_idx += 1
        if args.delay > 0:
            time.sleep(args.delay)

    cap.release()
    print(f"Posted {posted} unique event(s), skipped {skipped} duplicate frame(s)")


'''

t = t[:start] + new_block + t[end:]
p.write_text(t)
py_compile.compile(str(p), doraise=True)
print("FIXED - gate_sync.py syntax OK")
ENDFIX


