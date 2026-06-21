
cd ~/orange_pi_deploy
source venv/bin/activate
export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

date

python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5

for f in recordings/car_photos/*.mp4; do
  echo "Processing video: $f"
  python gate_sync.py --video "$f" --every 1 --max-frames 5 --preprocess none --delay 5
done




pip uninstall opencv-python-headless opencv-python -y
pip install opencv-python
python -c "import cv2; print('OpenCV OK:', hasattr(cv2, 'imshow'))"




sudo apt-get install -y v4l-utils
ls /dev/video*
v4l2-ctl --list-devices



ffmpeg -f v4l2 -input_format mjpeg -video_size 1280x720 -i /dev/video3 -frames:v 1 /tmp/test_cam.jpg -y
ls -lh /tmp/test_cam.jpg

ffmpeg -f v4l2 -input_format mjpeg -video_size 1280x720 -i /dev/video4 -frames:v 1 /tmp/test_cam.jpg -y
ls -lh /tmp/test_cam.jpg


cd ~/orange_pi_deploy
source venv/bin/activate

python run_webcam.py --camera 3 --width 1280 --height 720 --preprocess none --skip 2

python run_webcam.py --camera 4 --width 1280 --height 720 --preprocess none --skip 2

export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

python gate_sync.py --webcam --camera 3 --interval 15 --preprocess none











  
done
