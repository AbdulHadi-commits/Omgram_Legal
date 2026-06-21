sudo tee /etc/systemd/system/tailscaled.service.d/override.conf << 'EOF'
[Service]
ExecStart=
ExecStart=/usr/sbin/tailscaled --state=/var/lib/tailscale/tailscaled.state --socket=/run/tailscale/tailscaled.sock --port=41641 --tun=userspace-networking
EOF

sudo systemctl daemon-reload
sudo systemctl restart tailscaled
sudo systemctl status tailscaled --no-pager -l



sudo tailscale up --hostname=orange-pi-fyp --netfilter-mode=off
