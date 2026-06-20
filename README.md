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




hadi@hadi-desktop:~$ cd ~/orange_pi_deploy
source venv/bin/activate
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 3
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 149
    print(f"Video: {path.name} — sample every {frame_step} frame(s), dedupe by plate per video
          ^
SyntaxError: unterminated f-string literal (detected at line 149)
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 


