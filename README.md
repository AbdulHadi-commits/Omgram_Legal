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


venv) hadi@hadi-desktop:~/orange_pi_deploy$ python gate_sync.py --folder recordings/car_photos/ --preprocess auto
Loading models on Pi...
Device: cpu
Plate detector : /home/hadi/orange_pi_deploy/models/plate_best.pt
Char recognizer: /home/hadi/orange_pi_deploy/models/char_best.pt
VMMR checkpoint: /home/hadi/orange_pi_deploy/models/efficientnet_b4_best.pth
VMMR classes   : 245
Load times (s): {'plate_detector': 0.06, 'char_recognizer': 0.06, 'vmmr_classifier': 1.07}

Syncing 20 image(s) to Live Feed

Pipeline: DSC_1014_JPG.rf.8d3517f2b6b3c431921e79f0c7288b08.jpg
WARNING ⚠️ imgsz=[380] must be multiple of max stride 32, updating to [384]
  Plate   : MND-486
  Vehicle : Suzuki_Mehran (72.6%)
  Weather : rain
  Time    : 1619 ms
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
