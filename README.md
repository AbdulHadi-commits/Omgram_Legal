cd ~/orange_pi_deploy
sed -i 's/\r$//' setup_orangepi.sh record_video.sh
bash setup_orangepi.sh
source venv/bin/activate
pip install huggingface_hub requests
python download_models.py
python test_models.py



hadi@hadi-desktop:~/orange_pi_deploy$ sed -i 's/\r$//' setup_orangepi.sh record_video.sh 
hadi@hadi-desktop:~/orange_pi_deploy$ bash setup_orangepi.sh
==============================================
 FYP Orange Pi 5 Pro — Environment Setup
==============================================
Project root: /home/hadi

[1/5] Installing system dependencies...
[sudo] password for hadi: 
Hit:1 http://ports.ubuntu.com/ubuntu-ports noble InRelease                     
Hit:2 https://ppa.launchpadcontent.net/kisak/kisak-mesa/ubuntu noble InRelease 
Hit:3 http://ports.ubuntu.com/ubuntu-ports noble-backports InRelease
Hit:4 https://ppa.launchpadcontent.net/liujianfeng1994/chromium/ubuntu noble InRelease
Get:5 http://ports.ubuntu.com/ubuntu-ports noble-updates InRelease [126 kB]
Get:6 http://ports.ubuntu.com/ubuntu-ports noble-security InRelease [126 kB]
Reading package lists... Done     
E: Release file for http://ports.ubuntu.com/ubuntu-ports/dists/noble-updates/InRelease is not valid yet (invalid for another 10h 12min 40s). Updates for this repository will not be applied.
E: Release file for http://ports.ubuntu.com/ubuntu-ports/dists/noble-security/InRelease is not valid yet (invalid for another 26min 12s). Updates for this repository will not be applied.
hadi@hadi-desktop:~/orange_pi_deploy$ 
