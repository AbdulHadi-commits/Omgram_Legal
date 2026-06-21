sudo tailscale up --hostname=orange-pi-fyp


tailscale ip -4
tailscale status





(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 
sudo journalctl -u tailscaled -n 40 --no-pager -l
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: router: portUpdate(port=41641, network=udp6)
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: router: using firewall mode pref
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: magicsock: disco key = d:e558baee269f8da2
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: Creating WireGuard device...
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: Bringing WireGuard device up...
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: Bringing router up...
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: external route: up
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: router: default choosing iptables
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: router: updateMagicsockPort(port=41641, network=udp6) failed: could not setup netfilter: could not create new netfilter: could not get iptables version: exit status 1
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: router: portUpdate(port=41641, network=udp4)
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: router: using firewall mode pref
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: router: default choosing iptables
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: router: using firewall mode pref
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: router: updateMagicsockPort(port=41641, network=udp4) failed: could not setup netfilter: could not create new netfilter: could not get iptables version: exit status 1
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: router: default choosing iptables
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: wgengine.NewUserspaceEngine(tun "tailscale0") error: router.Up: setting netfilter mode: could not create new netfilter: could not get iptables version: exit status 1
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: flushing log.
Jun 21 15:29:11 hadi-desktop tailscaled[58487]: logger closing down
Jun 21 15:29:12 hadi-desktop tailscaled[58487]: tstun: tstun: awaiting Wrapper.Start call
Jun 21 15:29:12 hadi-desktop tailscaled[58487]: logtail: upload: log upload of 709 bytes compressed failed: Post "https://log.tailscale.com/c/tailnode.log.tailscale.io/d066b1f0bb9cb6602309fa914f4c6d956104aeaed09b2f2db593e1fad2ba6c52": context canceled
Jun 21 15:29:12 hadi-desktop tailscaled[58487]: getLocalBackend error: createEngine: router.Up: setting netfilter mode: could not create new netfilter: could not get iptables version: exit status 1
Jun 21 15:29:12 hadi-desktop systemd[1]: tailscaled.service: Main process exited, code=exited, status=1/FAILURE
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: TPM: error opening: stat /dev/tpmrm0: no such file or directory
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: logtail started
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: Program starting: v1.98.4-t9e69045b2-ged3a62f14, Go 1.26.3: []string{"/usr/sbin/tailscaled", "--cleanup"}
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: LogID: 43b217a4b9158a38921cdd0463330fbf8374d1a896064c542cdce80e93a3c7f3
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: logpolicy: using $STATE_DIRECTORY, "/var/lib/tailscale"
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: dns: [resolved-ping=yes rc=resolved resolved=file nm=yes nm-resolved=yes nm-safe=no resolv-conf-mode=stub ret=systemd-resolved]
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: dns: using "systemd-resolved" mode
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: creating dns cleanup: route ip+net: no such network interface
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: linuxfw: clear iptables: could not get iptables version: exit status 1
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: linuxfw: clear ip6tables: could not get iptables version: exit status 1
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: cleanup: list tables: socket: protocol not supported
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: flushing log.
Jun 21 15:29:12 hadi-desktop tailscaled[58664]: logger closing down
Jun 21 15:29:13 hadi-desktop tailscaled[58664]: logtail: upload: log upload of 1730 bytes compressed failed: Post "https://log.tailscale.com/c/tailnode.log.tailscale.io/d066b1f0bb9cb6602309fa914f4c6d956104aeaed09b2f2db593e1fad2ba6c52": context canceled
Jun 21 15:29:13 hadi-desktop systemd[1]: tailscaled.service: Failed with result 'exit-code'.
Jun 21 15:29:13 hadi-desktop systemd[1]: tailscaled.service: Start request repeated too quickly.
Jun 21 15:29:13 hadi-desktop systemd[1]: tailscaled.service: Failed with result 'exit-code'.
Jun 21 15:29:13 hadi-desktop systemd[1]: Failed to start tailscaled.service - Tailscale node agent.
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 

