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

python3 << 'PATCH'
from pathlib import Path
import re

p = Path("gate_sync.py")
t = p.read_text()

t = re.sub(r"timeout=\d+", "timeout=180", t)
t = re.sub(r"retries=\d+", "retries=5", t)
t = re.sub(r"max_side: int = \d+", "max_side: int = 480", t)
t = re.sub(r"quality: int = \d+", "quality: int = 55", t)
t = re.sub(r"400_000", "250_000", t)

if "--skip" not in t:
    t = t.replace(
        'parser.add_argument("--delay"',
        'parser.add_argument("--skip", type=int, default=0, help="Folder: skip first N images")\n'
        '    parser.add_argument("--upload-timeout", type=int, default=180)\n'
        '    parser.add_argument("--retries", type=int, default=5)\n'
        '    parser.add_argument("--delay"'
    )

if "args.skip" not in t and "def sync_folder" in t:
    t = t.replace(
        'print(f"Syncing {len(images)} image(s) to Live Feed\\n")',
        'if args.skip > 0:\n'
        '        images = images[args.skip:]\n'
        '        print(f"Skipping first {args.skip}, {len(images)} remaining\\n")\n'
        '    print(f"Syncing {len(images)} image(s) to Live Feed\\n"'
    )

# Ensure sync_image does not crash the whole folder on one failure
if "return False" not in t.split("def sync_image")[1].split("def sync_folder")[0]:
    old = "    site = post_to_vercel(args.api, args.gate_token, result, dry_run=args.dry_run)\n"
    new = (
        "    try:\n"
        "        site = post_to_vercel(args.api, args.gate_token, result, dry_run=args.dry_run)\n"
        "        print(f\"  Website : event id {site.get('event', {}).get('id')} -> {site.get('gate_action')}\\n\")\n"
        "        return True\n"
        "    except Exception as err:\n"
        "        print(f\"  Website : FAILED ({err})\\n\")\n"
        "        return False\n"
    )
    if old in t:
        t = t.replace(
            old + '        print(f"  Website : event id {site.get(\'event\', {}).get(\'id\')} → {site.get(\'gate_action\')}\\n")\n        return True\n    except Exception as err:\n        print(f"  Website : FAILED ({err})\\n")\n        return False\n',
            new
        )

p.write_text(t)
import py_compile
py_compile.compile(str(p), doraise=True)
print("Upload fix applied OK")
PATCH

