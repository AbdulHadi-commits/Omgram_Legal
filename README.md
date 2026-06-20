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




scp "d:\fyp-complete\FYP COMPLETE\orange_pi_deploy\gate_sync.py" hadi@YOUR_PI_IP:~/orange_pi_deploy/gate_sync.py
python3 -m py_compile ~/orange_pi_deploy/gate_sync.py && echo OK
cp ~/orange_pi_deploy/gate_sync.py.broken ~/orange_pi_deploy/gate_sync.py
