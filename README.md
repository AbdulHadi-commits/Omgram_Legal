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
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 
