sudo tailscale up --hostname=orange-pi-fyp


tailscale ip -4
tailscale status




(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 
sudo systemctl enable tailscaled
sudo systemctl start tailscaled
sudo systemctl status tailscaled --no-pager
Job for tailscaled.service failed because the control process exited with error code.
See "systemctl status tailscaled.service" and "journalctl -xeu tailscaled.service" for details.
× tailscaled.service - Tailscale node agent
     Loaded: loaded (/usr/lib/systemd/system/tailscaled.service; enabled; preset: enabled)
     Active: failed (Result: exit-code) since Sun 2026-06-21 15:29:13 EDT; 72ms ago
   Duration: 1.327s
       Docs: https://tailscale.com/docs/
    Process: 58487 ExecStart=/usr/sbin/tailscaled --state=/var/lib/tailscale/tailscaled.state --socket=/run/tailscale/tailscaled.sock --port=${PORT} $FLAGS (code=exited, status=1/FAILURE)
    Process: 58664 ExecStopPost=/usr/sbin/tailscaled --cleanup (code=exited, status=0/SUCCESS)
   Main PID: 58487 (code=exited, status=1/FAILURE)
        CPU: 165ms

Jun 21 15:29:13 hadi-desktop systemd[1]: tailscaled.service: Start reques…kly.
Jun 21 15:29:13 hadi-desktop systemd[1]: tailscaled.service: Failed with …de'.
Jun 21 15:29:13 hadi-desktop systemd[1]: Failed to start tailscaled.servi…ent.
Hint: Some lines were ellipsized, use -l to show in full.
(venv) hadi@hadi-desktop:~/orange_pi_deploy$ 

