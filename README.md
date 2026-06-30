cd ~/orange_pi_deploy
source venv/bin/activate

export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

ls recordings/car_photos/

python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5



# === Orange Pi: connect to phone hotspot + enable SSH ===

# 1) Connect to mobile hotspot "hadi"
nmcli device wifi connect "hadi" password "hadi1234" || \
nmcli device wifi connect "hadi" password "hadi1234" ifname wlan0

# 2) Save hotspot so Pi reconnects automatically next time
nmcli connection add type wifi con-name "hadi-hotspot" ifname wlan0 ssid "hadi" wifi-sec.key-mgmt wpa-psk wifi-sec.psk "hadi1234" 2>/dev/null || true
nmcli connection up "hadi-hotspot" 2>/dev/null || true

# 3) Install and start SSH server
sudo apt update
sudo apt install -y openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh

# 4) Allow SSH through firewall (safe if ufw not installed)
sudo ufw allow ssh 2>/dev/null || true

# 5) Show Pi IP — use this on your laptop: ssh hadi@THIS_IP
echo ""
echo "=== Pi IP address (copy the first number) ==="
hostname -I
echo ""
echo "=== SSH status ==="
sudo systemctl status ssh --no-pager | head -5
