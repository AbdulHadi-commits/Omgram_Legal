cd ~/orange_pi_deploy
source venv/bin/activate

export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

ls recordings/car_photos/

python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5



hadi@hadi-desktop:~$ nmcli device wifi connect "hadi" password "hadi1234" || \
nmcli device wifi connect "hadi" password "hadi1234" ifname wlan0
Error: No network with SSID 'hadi' found.
Error: No network with SSID 'hadi' found.
hadi@hadi-desktop:~$ nmcli device wifi connect "Hadi" password "hadi1234" || \
nmcli device wifi connect "hadi" password "hadi1234" ifname wlan0
Device 'wlan0' successfully activated with '5929d44f-b0d3-4c5c-92f5-d29c79356538'.
hadi@hadi-desktop:~$ nmcli connection add type wifi con-name "hadi-hotspot" ifname wlan0 ssid "Hadi" wifi-sec.key-mgmt wpa-psk wifi-sec.psk "hadi1234" 2>/dev/null || true
nmcli connection up "hadi-hotspot" 2>/dev/null || true
Connection 'hadi-hotspot' (ce4f3d69-0f3b-45fa-86c4-c6f601efd1f3) successfully added.
Connection successfully activated (D-Bus active path: /org/freedesktop/NetworkManager/ActiveConnection/9)
hadi@hadi-desktop:~$ sudo apt update
sudo apt install -y openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh
[sudo] password for hadi: 
Hit:1 http://ports.ubuntu.com/ubuntu-ports noble InRelease                     
Hit:2 https://ppa.launchpadcontent.net/kisak/kisak-mesa/ubuntu noble InRelease 
Get:3 http://ports.ubuntu.com/ubuntu-ports noble-updates InRelease [126 kB]
Get:4 https://pkgs.tailscale.com/stable/ubuntu noble InRelease              
Hit:5 https://ppa.launchpadcontent.net/liujianfeng1994/chromium/ubuntu noble InRelease
Get:6 https://pkgs.tailscale.com/stable/ubuntu noble/main arm64 Packages [14.8 kB]
Get:7 http://ports.ubuntu.com/ubuntu-ports noble-backports InRelease [126 kB]
Get:8 http://ports.ubuntu.com/ubuntu-ports noble-security InRelease [126 kB]
Get:9 http://ports.ubuntu.com/ubuntu-ports noble-updates/main arm64 Packages [1,070 kB]
Get:10 http://ports.ubuntu.com/ubuntu-ports noble-updates/main Translation-en [261 kB]
Get:11 http://ports.ubuntu.com/ubuntu-ports noble-updates/main arm64 Components [178 kB]
Get:12 http://ports.ubuntu.com/ubuntu-ports noble-updates arm64 Contents (deb) [69.8 MB]
Get:13 http://ports.ubuntu.com/ubuntu-ports noble-updates/main arm64 c-n-f Metadata [17.2 kB]
Get:14 http://ports.ubuntu.com/ubuntu-ports noble-updates/restricted arm64 Packages [1,699 kB]
Get:15 http://ports.ubuntu.com/ubuntu-ports noble-updates/restricted Translation-en [257 kB]
Get:16 http://ports.ubuntu.com/ubuntu-ports noble-updates/universe arm64 Packages [1,653 kB]
Get:17 http://ports.ubuntu.com/ubuntu-ports noble-updates/universe Translation-en [326 kB]
Get:18 http://ports.ubuntu.com/ubuntu-ports noble-updates/universe arm64 Components [387 kB]
Get:19 http://ports.ubuntu.com/ubuntu-ports noble-updates/universe arm64 c-n-f Metadata [33.4 kB]
Get:20 http://ports.ubuntu.com/ubuntu-ports noble-backports/main arm64 Components [3,572 B]
Get:21 http://ports.ubuntu.com/ubuntu-ports noble-backports/universe arm64 Components [10.5 kB]
Get:22 http://ports.ubuntu.com/ubuntu-ports noble-security/main arm64 Packages [824 kB]
Get:23 http://ports.ubuntu.com/ubuntu-ports noble-security/main Translation-en [179 kB]
Get:24 http://ports.ubuntu.com/ubuntu-ports noble-security/main arm64 Components [41.8 kB]
Get:25 http://ports.ubuntu.com/ubuntu-ports noble-security arm64 Contents (deb) [65.5 MB]
Get:26 http://ports.ubuntu.com/ubuntu-ports noble-security/main arm64 c-n-f Metadata [11.3 kB]
Get:27 http://ports.ubuntu.com/ubuntu-ports noble-security/restricted arm64 Packages [1,625 kB]
Get:28 http://ports.ubuntu.com/ubuntu-ports noble-security/restricted Translation-en [245 kB]
Get:29 http://ports.ubuntu.com/ubuntu-ports noble-security/universe arm64 Packages [1,201 kB]
Get:30 http://ports.ubuntu.com/ubuntu-ports noble-security/universe Translation-en [229 kB]
Get:31 http://ports.ubuntu.com/ubuntu-ports noble-security/universe arm64 Components [76.3 kB]
Get:32 http://ports.ubuntu.com/ubuntu-ports noble-security/universe arm64 c-n-f Metadata [23.6 kB]
Fetched 146 MB in 2min 6s (1,159 kB/s)                                         
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
532 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cloud-guest-utils eatmydata gdisk libeatmydata1 libfile-fnmatch-perl
  libgl1-amber-dri libglapi-mesa libllvm17t64 libllvm19 libxcb-dri2-0
  python-babel-localedata python3-attr python3-babel python3-configobj
  python3-jinja2 python3-json-pointer python3-jsonpatch python3-jsonschema
  python3-pyrsistent python3-serial python3-tz
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  openssh-client openssh-sftp-server
Suggested packages:
  keychain libpam-ssh monkeysphere ssh-askpass molly-guard ufw
Recommended packages:
  ssh-import-id
The following packages will be upgraded:
  openssh-client openssh-server openssh-sftp-server
3 upgraded, 0 newly installed, 0 to remove and 529 not upgraded.
Need to get 1,427 kB of archives.
After this operation, 64.5 kB disk space will be freed.
Get:1 http://ports.ubuntu.com/ubuntu-ports noble-updates/main arm64 openssh-sftp-server arm64 1:9.6p1-3ubuntu13.16 [36.8 kB]
Get:2 http://ports.ubuntu.com/ubuntu-ports noble-updates/main arm64 openssh-server arm64 1:9.6p1-3ubuntu13.16 [501 kB]
Get:3 http://ports.ubuntu.com/ubuntu-ports noble-updates/main arm64 openssh-client arm64 1:9.6p1-3ubuntu13.16 [889 kB]
Fetched 1,427 kB in 2s (871 kB/s)       
Preconfiguring packages ...
(Reading database ... 124779 files and directories currently installed.)
Preparing to unpack .../openssh-sftp-server_1%3a9.6p1-3ubuntu13.16_arm64.deb ...
Unpacking openssh-sftp-server (1:9.6p1-3ubuntu13.16) over (1:9.6p1-3ubuntu13.5) 
...
Preparing to unpack .../openssh-server_1%3a9.6p1-3ubuntu13.16_arm64.deb ...
Unpacking openssh-server (1:9.6p1-3ubuntu13.16) over (1:9.6p1-3ubuntu13.5) ...
Preparing to unpack .../openssh-client_1%3a9.6p1-3ubuntu13.16_arm64.deb ...
Unpacking openssh-client (1:9.6p1-3ubuntu13.16) over (1:9.6p1-3ubuntu13.5) ...
Setting up openssh-client (1:9.6p1-3ubuntu13.16) ...
Setting up openssh-sftp-server (1:9.6p1-3ubuntu13.16) ...
Setting up openssh-server (1:9.6p1-3ubuntu13.16) ...
Replacing config file /etc/ssh/sshd_config with new version
Processing triggers for man-db (2.12.0-4build2) ...
Synchronizing state of ssh.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install enable ssh
hadi@hadi-desktop:~$ # 4) Allow SSH through firewall (safe if ufw not installed) 
sudo ufw allow ssh 2>/dev/null || true

# 5) Show Pi IP — use this on your laptop: ssh hadi@THIS_IP
echo ""
echo "=== Pi IP address (copy the first number) ==="
hostname -I
echo ""
echo "=== SSH status ==="
sudo systemctl status ssh --no-pager | head -5

=== Pi IP address (copy the first number) ===
10.15.155.131 2404:3100:18a9:d62b:8feb:1b0d:125d:e427 2404:3100:18a9:d62b:8332:212c:1b65:54e8 

=== SSH status ===
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enabled)
     Active: active (running) since Tue 2026-06-30 07:34:46 EDT; 28s ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
hadi@hadi-desktop:~$ 

