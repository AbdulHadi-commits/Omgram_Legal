curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up --hostname=orange-pi-fyp

tailscale ip -4

curl -fsSL https://tailscale.com/install.sh | sh



cd ~/Downloads
wget https://pkgs.tailscale.com/stable/ubuntu/noble/main/arm64/tailscale_1.98.4_arm64.deb
sudo dpkg -i tailscale_1.98.4_arm64.deb
sudo apt-get install -f -y
sudo tailscale up --hostname=orange-pi-fyp

tailscale version
