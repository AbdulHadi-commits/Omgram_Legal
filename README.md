
cd ~/Downloads
wget -O nomachine.deb "https://download.nomachine.com/download/8.14/Linux/nomachine_8.14.2_4_arm64.deb"
sudo dpkg -i nomachine.deb
sudo apt-get install -f -y



sudo /usr/NX/bin/nxserver --status



(venv) hadi@hadi-desktop:~/orange_pi_deploy$ sudo apt-get update
sudo apt-get install -y iptables iptables-nft nftables kmod

sudo modprobe ip_tables
sudo modprobe iptable_filter
sudo modprobe iptable_nat
sudo modprobe nf_tables 2>/dev/null || true

iptables --version
Get:1 https://pkgs.tailscale.com/stable/ubuntu noble InRelease                 
Hit:2 http://ports.ubuntu.com/ubuntu-ports noble InRelease                     
Hit:3 http://ports.ubuntu.com/ubuntu-ports noble-updates InRelease             
Hit:4 http://ports.ubuntu.com/ubuntu-ports noble-backports InRelease           
Hit:5 http://ports.ubuntu.com/ubuntu-ports noble-security InRelease            
Hit:6 https://ppa.launchpadcontent.net/kisak/kisak-mesa/ubuntu noble InRelease 
Hit:7 https://ppa.launchpadcontent.net/liujianfeng1994/chromium/ubuntu noble InRelease
Fetched 6,581 B in 18s (357 B/s)                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package iptables-nft
iptables: Failed to initialize nft: Protocol not supported
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ sudo mkdir -p /etc/systemd/system/tailscaled.service.d

sudo tee /etc/systemd/system/tailscaled.service.d/override.conf << 'EOF'
[Service]
ExecStart=
ExecStart=/usr/sbin/tailscaled --state=/var/lib/tailscale/tailscaled.state --socket=/run/tailscale/tailscaled.sock --port=41641 --netfilter-mode=off
EOF

sudo systemctl daemon-reload
sudo systemctl restart tailscaled
sudo systemctl status tailscaled --no-pager -l
[Service]
ExecStart=
ExecStart=/usr/sbin/tailscaled --state=/var/lib/tailscale/tailscaled.state --socket=/run/tailscale/tailscaled.sock --port=41641 --netfilter-mode=off
Job for tailscaled.service failed because the control process exited with error code.
See "systemctl status tailscaled.service" and "journalctl -xeu tailscaled.service" for details.
● tailscaled.service - Tailscale node agent
     Loaded: loaded (/usr/lib/systemd/system/tailscaled.service; enabled; preset: enabled)
    Drop-In: /etc/systemd/system/tailscaled.service.d
             └─override.conf
     Active: activating (auto-restart) (Result: exit-code) since Sun 2026-06-21 15:38:49 EDT; 56ms ago
       Docs: https://tailscale.com/docs/
    Process: 59550 ExecStart=/usr/sbin/tailscaled --state=/var/lib/tailscale/tailscaled.state --socket=/run/tailscale/tailscaled.sock --port=41641 --netfilter-mode=off (code=exited, status=2)
    Process: 59555 ExecStopPost=/usr/sbin/tailscaled --cleanup (code=exited, status=0/SUCCESS)
   Main PID: 59550 (code=exited, status=2)
        CPU: 87ms
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ sudo tee /etc/systemd/system/tailscaled.service.d/override.conf << 'EOF'
[Service]
ExecStart=
ExecStart=/usr/sbin/tailscaled --state=/var/lib/tailscale/tailscaled.state --socket=/run/tailscale/tailscaled.sock --port=41641 --tun=userspace-networking
EOF

sudo systemctl daemon-reload
sudo systemctl restart tailscaled
sudo systemctl status tailscaled --no-pager -l
[Service]
ExecStart=
ExecStart=/usr/sbin/tailscaled --state=/var/lib/tailscale/tailscaled.state --socket=/run/tailscale/tailscaled.sock --port=41641 --tun=userspace-networking
● tailscaled.service - Tailscale node agent
     Loaded: loaded (/usr/lib/systemd/system/tailscaled.service; enabled; preset: enabled)
    Drop-In: /etc/systemd/system/tailscaled.service.d
             └─override.conf
     Active: active (running) since Sun 2026-06-21 15:46:17 EDT; 65ms ago
       Docs: https://tailscale.com/docs/
   Main PID: 59904 (tailscaled)
     Status: "Needs login: "
      Tasks: 13 (limit: 18938)
     Memory: 12.9M (peak: 13.5M)
        CPU: 46ms
     CGroup: /system.slice/tailscaled.service
             └─59904 /usr/sbin/tailscaled --state=/var/lib/tailscale/tailscaled.state --socket=/run/tailscale/tailscaled.sock --port=41641 --tun=userspace-networking

Jun 21 15:46:17 hadi-desktop tailscaled[59904]: Backend: logs: be:43b217a4b9158a38921cdd0463330fbf8374d1a896064c542cdce80e93a3c7f3 fe:
Jun 21 15:46:17 hadi-desktop tailscaled[59904]: Switching ipn state NoState -> NeedsLogin (WantRunning=false, nm=false)
Jun 21 15:46:17 hadi-desktop tailscaled[59904]: blockEngineUpdates(true)
Jun 21 15:46:17 hadi-desktop tailscaled[59904]: health(warnable=wantrunning-false): error: Tailscale is stopped.
Jun 21 15:46:17 hadi-desktop tailscaled[59904]: wgengine: Reconfig: configuring router
Jun 21 15:46:17 hadi-desktop tailscaled[59904]: wgengine: Reconfig: user dialer
Jun 21 15:46:17 hadi-desktop tailscaled[59904]: wgengine: Reconfig: configuring DNS
Jun 21 15:46:17 hadi-desktop tailscaled[59904]: dns: Set: {DefaultResolvers:[] Routes:{} SearchDomains:[] Hosts:0}
Jun 21 15:46:17 hadi-desktop tailscaled[59904]: dns: Resolvercfg: {Routes:{} Hosts:0 LocalDomains:[]}
Jun 21 15:46:17 hadi-desktop tailscaled[59904]: dns: OScfg: {}
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ sudo tailscale up --hostname=orange-pi-fyp --netfilter-mode=off
Warning: netfilter=off; configure iptables yourself.

To authenticate, visit:

	https://login.tailscale.com/a/131f98b701357e

Success.
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ tailscale ip -4
tailscale status
100.117.223.106
100.117.223.106  orange-pi-fyp    abdulhaadihaq@  linux    -                           
100.92.42.99     desktop-1ldvo6j  abdulhaadihaq@  windows  -                           
100.120.197.16   desktop-u91vin9  abdulhaadihaq@  windows  offline, last seen 73d ago  
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ cd ~/Downloads
wget -O nomachine.deb "https://download.nomachine.com/download/8.14/Linux/nomachine_8.14.2_4_arm64.deb"
sudo dpkg -i nomachine.deb
sudo apt-get install -f -y
--2026-06-21 16:15:56--  https://download.nomachine.com/download/8.14/Linux/nomachine_8.14.2_4_arm64.deb
Resolving download.nomachine.com (download.nomachine.com)... 80.92.89.79
Connecting to download.nomachine.com (download.nomachine.com)|80.92.89.79|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://web9001.nomachine.com/download/8.14/Linux/nomachine_8.14.2_4_arm64.deb [following]
--2026-06-21 16:15:58--  https://web9001.nomachine.com/download/8.14/Linux/nomachine_8.14.2_4_arm64.deb
Resolving web9001.nomachine.com (web9001.nomachine.com)... 83.222.232.25
Connecting to web9001.nomachine.com (web9001.nomachine.com)|83.222.232.25|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://www.nomachine.com [following]
--2026-06-21 16:15:59--  https://www.nomachine.com/
Resolving www.nomachine.com (www.nomachine.com)... 80.92.83.99
Connecting to www.nomachine.com (www.nomachine.com)|80.92.83.99|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘nomachine.deb’

nomachine.deb           [   <=>             ] 157.36K   251KB/s    in 0.6s    

2026-06-21 16:16:03 (251 KB/s) - ‘nomachine.deb’ saved [161138]

[sudo] password for hadi: 
dpkg-deb: error: 'nomachine.deb' is not a Debian format archive
dpkg: error processing archive nomachine.deb (--install):
 dpkg-deb --control subprocess returned error exit status 2
Errors were encountered while processing:
 nomachine.deb
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
0 upgraded, 0 newly installed, 0 to remove and 528 not upgraded.
(venv) hadi@hadi-desktop:~/Downloads$ sudo /usr/NX/bin/nxserver --status
sudo: /usr/NX/bin/nxserver: command not found
(venv) hadi@hadi-desktop:~/Downloads$ 

