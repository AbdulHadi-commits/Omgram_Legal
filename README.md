cd ~/orange_pi_deploy
source venv/bin/activate


export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"


python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5


python gate_sync.py --video recordings/car_photos/myvideo.mp4 --every 1 --max-frames 5 --preprocess none --delay 5
