sudo tailscale up --hostname=orange-pi-fyp


tailscale ip -4
tailscale status




sudo journalctl -u tailscaled -n 40 --no-pager -l

