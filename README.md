cd ~/orange_pi_deploy
source venv/bin/activate


export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"


python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5


python gate_sync.py --video recordings/car_photos/myvideo.mp4 --every 1 --max-frames 5 --preprocess none --delay 5




(venv) hadi@hadi-desktop:~/orange_pi_deploy$ python gate_sync.py --video recordings/car_photos/myvideo.mp4 --every 1 --max-frames 5 --preprocess none --delay 5
Loading models on Pi...
Device: cpu
Plate detector : /home/hadi/orange_pi_deploy/models/plate_best.pt
Char recognizer: /home/hadi/orange_pi_deploy/models/char_best.pt
VMMR checkpoint: /home/hadi/orange_pi_deploy/models/efficientnet_b4_best.pth
VMMR classes   : 245
Load times (s): {'plate_detector': 0.06, 'char_recognizer': 0.06, 'vmmr_classifier': 1.08}

Cannot open video: recordings/car_photos/myvideo.mp4
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 

