cd ~/orange_pi_deploy
source venv/bin/activate
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="your-secret-from-vercel"
ls ~/orange_pi_deploy/recordings/car_photos/ | head -20
ls ~/orange_pi_deploy/recordings/car_photos/*.mp4
python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 3
for f in recordings/car_photos/*.mp4; do
  echo "Processing video: $f"
  python gate_sync.py --video "$f" --every 1 --max-frames 5 --preprocess none --delay 3
done



Vehicle : Toyota_yaris_gen 2018 2020 (56.2%)
  Weather : none
  Time    : 847 ms
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
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 101, in post_to_vercel
    response.raise_for_status()
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/requests/models.py", line 1167, in raise_for_status
    raise HTTPError(http_error_msg, response=self)
requests.exceptions.HTTPError: 401 Client Error: Unauthorized for url: https://automated-gate-access.vercel.app/api/gate/ingest
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 

