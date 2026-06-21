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
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 

