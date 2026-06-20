sudo apt-get update
sudo apt-get install -y v4l-utils ffmpeg

cd ~/orange_pi_deploy
source venv/bin/activate

pip uninstall opencv-python-headless -y
pip install opencv-python

export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

echo 'export GATE_API_URL="https://automated-gate-access.vercel.app/api"' >> ~/.bashrc
echo 'export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"' >> ~/.bashrc
source ~/.bashrc

