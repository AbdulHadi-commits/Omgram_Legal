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




(venv) hadi@hadi-desktop:~/orange_pi_deploy$ tailscale version
1.98.4
  tailscale commit: 9e69045b291a7cb1edc714442d68e83b95d05e6b
  long version: 1.98.4-t9e69045b2-ged3a62f14
  other commit: ed3a62f143dd73c8aae368d9c639ea49de878f9b
  go version: go1.26.3 (tailscale/go e877d97384)
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 

