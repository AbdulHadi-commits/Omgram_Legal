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

ls /dev/video*
v4l2-ctl --list-devices




cd ~/orange_pi_deploy
source venv/bin/activate
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

date

python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5

for f in recordings/car_photos/*.mp4; do
  python gate_sync.py --video "$f" --every 1 --max-frames 5 --preprocess none --delay 5










hadi@hadi-desktop:~/orange_pi_deploy$ python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5
Traceback (most recent call last):
  File "/home/hadi/orange_pi_deploy/gate_sync.py", line 46, in <module>
    from models_loader import load_all_models
  File "/home/hadi/orange_pi_deploy/models_loader.py", line 13, in <module>
    from ultralytics import YOLO
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/ultralytics/__init__.py", line 13, in <module>
    from ultralytics.utils import ASSETS, SETTINGS
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/ultralytics/utils/__init__.py", line 30, in <module>
    from ultralytics.utils.patches import imread, imshow, imwrite, torch_save  # for patches
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/hadi/orange_pi_deploy/venv/lib/python3.12/site-packages/ultralytics/utils/patches.py", line 18, in <module>
    _imshow = cv2.imshow  # copy to avoid recursion errors
              ^^^^^^^^^^
AttributeError: module 'cv2' has no attribute 'imshow'
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 


  
done
