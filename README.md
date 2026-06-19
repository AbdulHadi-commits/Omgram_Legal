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
