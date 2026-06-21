
cd ~/Downloads
wget -O nomachine.deb "https://download.nomachine.com/download/8.14/Linux/nomachine_8.14.2_4_arm64.deb"
sudo dpkg -i nomachine.deb
sudo apt-get install -f -y



sudo /usr/NX/bin/nxserver --status
