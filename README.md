
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
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 
