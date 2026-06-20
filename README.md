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




adi@hadi-desktop:~$ cd ~/orange_pi_deploy
source venv/bin/activate
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 3
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 149
    print(f"Video: {path.name} — sample every {frame_step} frame(s), dedupe by plate per video
          ^
SyntaxError: unterminated f-string literal (detected at line 149)
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ cd ~/orange_pi_deploy
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
ENDFIX"FIXED - gate_sync.py syntax OK"))(s), skipped {skipped} duplicate frame(s
FIXED - gate_sync.py syntax OK
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 3
Loading models on Pi...
Device: cpu
Plate detector : /home/hadi/orange_pi_deploy/models/plate_best.pt
Char recognizer: /home/hadi/orange_pi_deploy/models/char_best.pt
VMMR checkpoint: /home/hadi/orange_pi_deploy/models/efficientnet_b4_best.pth
VMMR classes   : 245
Load times (s): {'plate_detector': 0.07, 'char_recognizer': 0.06, 'vmmr_classifier': 1.11}

Syncing 48 image(s) to Live Feed

Pipeline: WIN_20260620_02_09_46_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : AAC-7396
  Vehicle : Toyota_yaris_gen 2018 2020 (56.2%)
  Weather : none
  Time    : 886 ms
  Website : event id 1 → closed

Pipeline: WIN_20260620_02_10_22_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : AAC-396
  Vehicle : Toyota_Corolla Axio 11th Generation (7.0%)
  Weather : none
  Time    : 747 ms
  Website : event id 2 → closed

Pipeline: WIN_20260620_02_11_00_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : BTY-8393
  Vehicle : Hyundai_Santro 2nd Generation (87.7%)
  Weather : none
  Time    : 728 ms
  Website : event id 3 → opened

Pipeline: WIN_20260620_02_11_12_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : AWC-049
  Vehicle : Honda_City 5th Generation (88.8%)
  Weather : none
  Time    : 736 ms
  Website : event id 4 → opened

Pipeline: WIN_20260620_02_11_54_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LEC-3800
  Vehicle : Suzuki_Swift 1st Generation (91.9%)
  Weather : none
  Time    : 791 ms
Traceback (most recent call last):
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/urllib3/connectionpool.py", line 534, in _make_request
    response = conn.getresponse()
               ^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/urllib3/connection.py", line 571, in getresponse
    httplib_response = super().getresponse()
                       ^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.12/http/client.py", line 1448, in getresponse
    response.begin()
  File "/usr/lib/python3.12/http/client.py", line 336, in begin
    version, status, reason = self._read_status()
                              ^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.12/http/client.py", line 297, in _read_status
    line = str(self.fp.readline(_MAXLINE + 1), "iso-8859-1")
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.12/socket.py", line 707, in readinto
    return self._sock.recv_into(b)
           ^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.12/ssl.py", line 1252, in recv_into
    return self.read(nbytes, buffer)
           ^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3.12/ssl.py", line 1104, in read
    return self._sslobj.read(len, buffer)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
TimeoutError: The read operation timed out

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/requests/adapters.py", line 696, in send
    resp = conn.urlopen(
           ^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/urllib3/connectionpool.py", line 842, in urlopen
    retries = retries.increment(
              ^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/urllib3/util/retry.py", line 498, in increment
    raise reraise(type(error), error, _stacktrace)
          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/urllib3/util/util.py", line 39, in reraise
    raise value
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/urllib3/connectionpool.py", line 788, in urlopen
    response = self._make_request(
               ^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/urllib3/connectionpool.py", line 536, in _make_request
    self._raise_timeout(err=e, url=url, timeout_value=read_timeout)
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/urllib3/connectionpool.py", line 367, in _raise_timeout
    raise ReadTimeoutError(
urllib3.exceptions.ReadTimeoutError: HTTPSConnectionPool(host='automated-gate-access.vercel.app', port=443): Read timed out. (read timeout=90)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 289, in <module>
    raise SystemExit(main())
                     ^^^^^^
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 280, in main
    sync_folder(Path(args.folder), models, args)
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 135, in sync_folder
    sync_image(img, models, args)
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 123, in sync_image
    site = post_to_vercel(args.api, args.gate_token, result, dry_run=args.dry_run)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 95, in post_to_vercel
    response = requests.post(
               ^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/requests/api.py", line 134, in post
    return request("post", url, data=data, json=json, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/requests/api.py", line 71, in request
    return session.request(method=method, url=url, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/requests/sessions.py", line 651, in request
    resp = self.send(prep, **send_kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/requests/sessions.py", line 784, in send
    r = adapter.send(request, **kwargs)
        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/requests/adapters.py", line 742, in send
    raise ReadTimeout(e, request=request)
requests.exceptions.ReadTimeout: HTTPSConnectionPool(host='automated-gate-access.vercel.app', port=443): Read timed out. (read timeout=90)
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 

