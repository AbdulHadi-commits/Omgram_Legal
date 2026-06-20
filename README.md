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

curl -fsSL -o gate_sync.py \
  https://raw.githubusercontent.com/AbdullahYaseen01/webfyp/main/pi/gate_sync.py

curl -fsSL -o preprocessing.py \
  https://raw.githubusercontent.com/AbdullahYaseen01/webfyp/main/pi/preprocessing.py

curl -fsSL -o pipeline.py \
  https://raw.githubusercontent.com/AbdullahYaseen01/webfyp/main/pi/pipeline.py

sed -i 's/\r$//' gate_sync.py preprocessing.py pipeline.py

echo "Updated OK"
grep -n "_event_dedup_key" gate_sync.py


