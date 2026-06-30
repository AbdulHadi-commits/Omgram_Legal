cd ~/orange_pi_deploy
source venv/bin/activate

export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

ls recordings/car_photos/

python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5



# === Orange Pi: auto-connect to phone hotspot "Hadi" (run once) ===

# 1) Turn Wi-Fi on
sudo nmcli radio wifi on

# 2) Remove old/broken profiles (safe if missing)
sudo nmcli connection delete hadi-hotspot 2>/dev/null || true
sudo nmcli connection delete hadi 2>/dev/null || true

# 3) Create saved profile (SSID is case-sensitive: Hadi)
sudo nmcli connection add type wifi con-name "hadi-hotspot" ifname wlan0 ssid "Hadi" \
  wifi-sec.key-mgmt wpa-psk wifi-sec.psk "hadi1234"

# 4) Auto-connect on boot + prefer this network
sudo nmcli connection modify hadi-hotspot connection.autoconnect yes
sudo nmcli connection modify hadi-hotspot connection.autoconnect-priority 999
sudo nmcli connection modify hadi-hotspot connection.autoconnect-retries -1

# 5) Keep Wi-Fi awake (helps phone hotspots)
sudo nmcli connection modify hadi-hotspot 802-11-wireless.powersave 2

# 6) Connect now
sudo nmcli connection up hadi-hotspot

# 7) Verify
echo ""
echo "=== Check these ==="
nmcli connection show hadi-hotspot | grep autoconnect
nmcli connection show --active



sudo reboot
hostname -I

