curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up --hostname=orange-pi-fyp

tailscale ip -4


(venv) hadi@hadi-desktop:~/orange_pi_deploy$ curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up --hostname=orange-pi-fyp
Installing Tailscale for ubuntu noble, using method apt
+ sudo mkdir -p --mode=0755 /usr/share/keyrings
[sudo] password for hadi: 
+ curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/noble.noarmor.gpg
+ sudo tee /usr/share/keyrings/tailscale-archive-keyring.gpg
+ sudo chmod 0644 /usr/share/keyrings/tailscale-archive-keyring.gpg
+ + curl -fsSLsudo https://pkgs.tailscale.com/stable/ubuntu/noble.tailscale-keyring.list tee
 /etc/apt/sources.list.d/tailscale.list
curl: (35) OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to pkgs.tailscale.com:443 
+ sudo chmod 0644 /etc/apt/sources.list.d/tailscale.list
+ sudo apt-get update
Hit:1 http://ports.ubuntu.com/ubuntu-ports noble InRelease                   
Hit:2 https://ppa.launchpadcontent.net/kisak/kisak-mesa/ubuntu noble InRelease
Hit:3 https://ppa.launchpadcontent.net/liujianfeng1994/chromium/ubuntu noble InRelease
Get:4 http://ports.ubuntu.com/ubuntu-ports noble-updates InRelease [126 kB]
Get:5 http://ports.ubuntu.com/ubuntu-ports noble-backports InRelease [126 kB]
Get:6 http://ports.ubuntu.com/ubuntu-ports noble-security InRelease [126 kB]
Get:7 http://ports.ubuntu.com/ubuntu-ports noble-updates/main arm64 Packages [1,055 kB]
Get:8 http://ports.ubuntu.com/ubuntu-ports noble-updates/main arm64 Components [178 kB]
Get:9 http://ports.ubuntu.com/ubuntu-ports noble-updates/universe arm64 Packages [1,652 kB]
Get:10 http://ports.ubuntu.com/ubuntu-ports noble-updates/universe arm64 Components [387 kB]
Get:11 http://ports.ubuntu.com/ubuntu-ports noble-backports/main arm64 Components [3,568 B]
Get:12 http://ports.ubuntu.com/ubuntu-ports noble-backports/universe arm64 Components [10.5 kB]
Get:13 http://ports.ubuntu.com/ubuntu-ports noble-security/main arm64 Components [41.9 kB]
Get:14 http://ports.ubuntu.com/ubuntu-ports noble-security/universe arm64 Components [76.2 kB]
Fetched 3,782 kB in 19s (199 kB/s)                                           
Reading package lists... Done
+ [ -n  ]
+ sudo apt-get install -y tailscale tailscale-archive-keyring
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package tailscale
E: Unable to locate package tailscale-archive-keyring
sudo: tailscale: command not found
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 
