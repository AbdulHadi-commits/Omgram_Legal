unzip -o ~/Downloads/orange_pi_deploy_update.zip -d ~/orange_pi_deploy/
python3 -m py_compile ~/orange_pi_deploy/gate_sync.py ~/orange_pi_deploy/pipeline.py ~/orange_pi_deploy/preprocessing.py && echo OK

cd ~/orange_pi_deploy
source venv/bin/activate
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5
python gate_sync.py --video recordings/car_photos/WIN_20260620_02_18_38_Pro.mp4 --every 1 --max-frames 5 --preprocess none --delay 5



timedatectl
sudo timedatectl set-ntp true


