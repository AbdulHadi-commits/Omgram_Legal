
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



ffmpeg -f v4l2 -i /dev/video0 -frames:v 1 /tmp/test_cam.jpg -y
ls -lh /tmp/test._camjpg


python test_models.py

python run_webcam.py --camera 0 --width 1280 --height 720 --preprocess none --skip 2

python run_webcam.py --camera 1 --width 1280 --height 720 --preprocess none --skip 2

export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

python gate_sync.py --webcam --camera 0 --interval 15 --preprocess none




(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 
sudo apt-get install -y v4l-utils
ls /dev/video*
v4l2-ctl --list-devices
[sudo] password for hadi: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
v4l-utils is already the newest version (1.26.1-4build3).
The following packages were automatically installed and are no longer required:
  cloud-guest-utils eatmydata gdisk libeatmydata1 libfile-fnmatch-perl
  libgl1-amber-dri libglapi-mesa libllvm17t64 libllvm19 libxcb-dri2-0
  python-babel-localedata python3-attr python3-babel python3-configobj
  python3-jinja2 python3-json-pointer python3-jsonpatch python3-jsonschema
  python3-pyrsistent python3-serial python3-tz
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 528 not upgraded.
/dev/video0  /dev/video1  /dev/video2  /dev/video3  /dev/video4
rockchip,rk3568-vpu-dec (platform:fdb50000.video-codec):
	/dev/video0
	/dev/media0

rockchip,rk3588-vepu121-enc (platform:fdba0000.video-codec):
	/dev/video1
	/dev/media1

rockchip,rk3588-av1-vpu-dec (platform:fdc70000.video-codec):
	/dev/video2
	/dev/media2

WEBCAM: WEBCAM (usb-xhci-hcd.5.auto-1):
	/dev/video3
	/dev/video4
	/dev/media3

(venv) hadi@hadi-desktop:~/orange_pi_deploy$ ffmpeg -f v4l2 -i /dev/video0 -frames:v 1 /tmp/test_cam.jpg -y
ls -lh /tmp/test._camjpg
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
[video4linux2,v4l2 @ 0xaaaace036e50] Not a video capture device.
[in#0 @ 0xaaaace036d50] Error opening input: No such device
Error opening input file /dev/video0.
Error opening input files: No such device
ls: cannot access '/tmp/test._camjpg': No such file or directory
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 







  
done
