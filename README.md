
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"
cd ~/orange_pi_deploy
ls ~/orange_pi_deploy/recordings/car_photos/ | head -20
ls ~/orange_pi_deploy/recordings/car_photos/*.mp4
python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 3
for f in recordings/car_photos/*.mp4; do
  echo "Processing video: $f"
  python gate_sync.py --video "$f" --every 1 --max-frames 5 --preprocess none --delay 3
done





venv) hadi@hadi-desktop:~/orange_pi_deploy$ python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 3
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
  Time    : 915 ms
Traceback (most recent call last):
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 245, in <module>
    raise SystemExit(main())
                     ^^^^^^
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 236, in main
    sync_folder(Path(args.folder), models, args)
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 110, in sync_folder
    sync_image(img, models, args)
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 98, in sync_image
    site = post_to_vercel(args.api, args.gate_token, result, dry_run=args.dry_run)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 90, in post_to_vercel
    response.raise_for_status()
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/requests/models.py", line 1167, in raise_for_status
    raise HTTPError(http_error_msg, response=self)
requests.exceptions.HTTPError: 413 Client Error: Request Entity Too Large for url: https://automated-gate-access.vercel.app/api/gate/ingest
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 

