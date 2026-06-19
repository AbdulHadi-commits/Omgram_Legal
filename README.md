cd ~/orange_pi_deploy
source venv/bin/activate
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

echo 'export GATE_API_URL="https://automated-gate-access.vercel.app/api"' >> ~/.bashrc
echo 'export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"' >> ~/.bashrc
source ~/.bashrc

curl -s -X POST "$GATE_API_URL/gate/ingest" \
  -H "Content-Type: application/json" \
  -H "X-Gate-Token: $GATE_DEVICE_TOKEN" \
  -d '{"plate_texts":["TEST123"],"vehicle_label":"Toyota_Corolla","vehicle_conf":0.95,"preprocess_mode":"none"}'

  cd ~/orange_pi_deploy
source venv/bin/activate
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

python gate_sync.py --folder recordings/car_photos/ --preprocess auto


(venv) hadi@hadi-desktop:~/orange_pi_deploy$ python gate_sync.py --folder recordings/car_photos/ --preprocess auto
Loading models on Pi...
Device: cpu
Plate detector : /home/hadi/orange_pi_deploy/models/plate_best.pt
Char recognizer: /home/hadi/orange_pi_deploy/models/char_best.pt
VMMR checkpoint: /home/hadi/orange_pi_deploy/models/efficientnet_b4_best.pth
VMMR classes   : 245
Load times (s): {'plate_detector': 0.07, 'char_recognizer': 0.06, 'vmmr_classifier': 1.11}

Syncing 20 image(s) to Live Feed

Pipeline: DSC_1014_JPG.rf.8d3517f2b6b3c431921e79f0c7288b08.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : MND-486
  Vehicle : Suzuki_Mehran (72.6%)
  Weather : rain
  Time    : 1692 ms
  Website : event id 101 → closed

Pipeline: DSC_1015_JPG.rf.76977f4a1dd5f0fe90eec6946c256c91.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : MND-486
  Vehicle : Suzuki_Mehran (94.3%)
  Weather : rain
  Time    : 1587 ms
  Website : event id 102 → opened

Pipeline: DSC_1018_JPG.rf.dac3c3a36d94e6b9a733bae53f265ad8.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LEJ-1637
  Vehicle : Toyota_hilux_gen 2015 2020 (39.6%)
  Weather : rain
  Time    : 1502 ms
  Website : event id 103 → closed

Pipeline: DSC_1018_JPG.rf.e2901d8a654e11771ddb41bae42adee8.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : LEJ-1637
  Vehicle : Toyota_hilux_gen 2015 2020 (39.1%)
  Weather : rain
  Time    : 1440 ms
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
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 256, in <module>
    raise SystemExit(main())
                     ^^^^^^
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 247, in main
    sync_folder(Path(args.folder), models, args)
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 121, in sync_folder
    sync_image(img, models, args)
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 109, in sync_image
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
