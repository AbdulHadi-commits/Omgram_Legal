sudo tailscale up --hostname=orange-pi-fyp


tailscale ip -4
tailscale status





sudo systemctl enable tailscaled
sudo systemctl start tailscaled
sudo systemctl status tailscaled --no-pager
