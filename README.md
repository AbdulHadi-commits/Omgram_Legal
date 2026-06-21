for f in recordings/car_photos/*.mp4; do
  python gate_sync.py --video "$f" --every 1 --max-frames 5 --preprocess none --delay 5
done
