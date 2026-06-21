
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




(venv) hadi@hadi-desktop:~/orange_pi_deploy$ ffmpeg -f v4l2 -input_format mjpeg -video_size 1280x720 -i /dev/video3 -frames:v 1 /tmp/test_cam.jpg -y
ls -lh /tmp/test_cam.jpg
ffmpeg version 6.1.1-3ubuntu5 Copyright (c) 2000-2023 the FFmpeg developers
  built with gcc 13 (Ubuntu 13.2.0-23ubuntu3)
  configuration: --prefix=/usr --extra-version=3ubuntu5 --toolchain=hardened --libdir=/usr/lib/aarch64-linux-gnu --incdir=/usr/include/aarch64-linux-gnu --arch=arm64 --enable-gpl --disable-stripping --disable-omx --enable-gnutls --enable-libaom --enable-libass --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libcodec2 --enable-libdav1d --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libglslang --enable-libgme --enable-libgsm --enable-libharfbuzz --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-librubberband --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libtheora --enable-libtwolame --enable-libvidstab --enable-libvorbis --enable-libvpx --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzimg --enable-openal --enable-opencl --enable-opengl --disable-sndio --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-ladspa --enable-libbluray --enable-libjack --enable-libpulse --enable-librabbitmq --enable-librist --enable-libsrt --enable-libssh --enable-libsvtav1 --enable-libx264 --enable-libzmq --enable-libzvbi --enable-lv2 --enable-sdl2 --enable-libplacebo --enable-librav1e --enable-pocketsphinx --enable-librsvg --enable-libjxl --enable-shared
  libavutil      58. 29.100 / 58. 29.100
  libavcodec     60. 31.102 / 60. 31.102
  libavformat    60. 16.100 / 60. 16.100
  libavdevice    60.  3.100 / 60.  3.100
  libavfilter     9. 12.100 /  9. 12.100
  libswscale      7.  5.100 /  7.  5.100
  libswresample   4. 12.100 /  4. 12.100
  libpostproc    57.  3.100 / 57.  3.100
Input #0, video4linux2,v4l2, from '/dev/video3':
  Duration: N/A, start: 2508.645117, bitrate: N/A
  Stream #0:0: Video: mjpeg (Baseline), yuvj422p(pc, bt470bg/unknown/unknown), 1280x720, 30 fps, 30 tbr, 1000k tbn
Stream mapping:
  Stream #0:0 -> #0:0 (mjpeg (native) -> mjpeg (native))
Press [q] to stop, [?] for help
Output #0, image2, to '/tmp/test_cam.jpg':
  Metadata:
    encoder         : Lavf60.16.100
  Stream #0:0: Video: mjpeg, yuvj422p(pc, bt470bg/unknown/unknown, progressive), 1280x720, q=2-31, 200 kb/s, 30 fps, 30 tbn
    Metadata:
      encoder         : Lavc60.31.102 mjpeg
    Side data:
      cpb: bitrate max/min/avg: 0/0/200000 buffer size: 0 vbv_delay: N/A
frame=    0 fps=0.0 q=2.2 size=       0kB time=00:00:00.00 bitrate=N/A speed=   [image2 @ 0xaaaac5499940] The specified filename '/tmp/test_cam.jpg' does not contain an image sequence pattern or a pattern is invalid.
[image2 @ 0xaaaac5499940] Use a pattern such as %03d for an image sequence or use the -update option (with -frames:v 1 if needed) to write a single image.
[out#0/image2 @ 0xaaaac549a390] video:37kB audio:0kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: unknown
frame=    1 fps=0.0 q=2.2 Lsize=N/A time=00:00:00.00 bitrate=N/A speed=   0x    
-rw-rw-r-- 1 hadi hadi 38K Jun 21 13:37 /tmp/test_cam.jpg
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 







  
done
