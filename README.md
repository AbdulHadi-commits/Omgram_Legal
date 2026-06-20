
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






hadi@hadi-desktop:~$ cd ~/orange_pi_deploy
source venv/bin/activate
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ python3 -m py_compile ~/orange_pi_deploy/gate_sync.py && echo OK
OK
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 
python gate_sync.py --folder recordings/car_photos/ --preprocess auto --delay 5
Loading models on Pi...
Device: cpu
Plate detector : /home/hadi/orange_pi_deploy/models/plate_best.pt
Char recognizer: /home/hadi/orange_pi_deploy/models/char_best.pt
VMMR checkpoint: /home/hadi/orange_pi_deploy/models/efficientnet_b4_best.pth
VMMR classes   : 245
Load times (s): {'plate_detector': 0.07, 'char_recognizer': 0.06, 'vmmr_classifier': 1.1}

Syncing 48 image(s) to Live Feed

Pipeline: WIN_20260620_02_09_46_Pro.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
Traceback (most recent call last):
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 300, in <module>
    raise SystemExit(main())
                     ^^^^^^
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 291, in main
    sync_folder(Path(args.folder), models, args)
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 153, in sync_folder
    if sync_image(img, models, args):
       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 133, in sync_image
    _print_result(result)
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 245, in _print_result
    if result.weather_confidence:
       ^^^^^^^^^^^^^^^^^^^^^^^^^
AttributeError: 'PipelineResult' object has no attribute 'weather_confidence'
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 

