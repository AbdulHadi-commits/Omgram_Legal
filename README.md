sudo apt-get update
sudo apt-get install -y iptables iptables-nft nftables kmod

sudo modprobe ip_tables
sudo modprobe iptable_filter
sudo modprobe iptable_nat
sudo modprobe nf_tables 2>/dev/null || true

iptables --version


sudo systemctl restart tailscaled
sudo systemctl status tailscaled --no-pager -l

sudo tailscale up --hostname=orange-pi-fyp
tailscale ip -4


sudo mkdir -p /etc/systemd/system/tailscaled.service.d

sudo tee /etc/systemd/system/tailscaled.service.d/override.conf << 'EOF'
[Service]
ExecStart=
ExecStart=/usr/sbin/tailscaled --state=/var/lib/tailscale/tailscaled.state --socket=/run/tailscale/tailscaled.sock --port=41641 --netfilter-mode=off
EOF

sudo systemctl daemon-reload
sudo systemctl restart tailscaled
sudo systemctl status tailscaled --no-pager -l


sudo tailscale up --hostname=orange-pi-fyp
tailscale ip -4
tailscale status

