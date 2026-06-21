cd ~/orange_pi_deploy
source venv/bin/activate


export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"


python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5


python gate_sync.py --video recordings/car_photos/myvideo.mp4 --every 1 --max-frames 5 --preprocess none --delay 5





sudo sed -i 's/#WaylandEnable=false/WaylandEnable=false/' /etc/gdm3/custom.conf 2>/dev/null
grep -q '^WaylandEnable=false' /etc/gdm3/custom.conf 2>/dev/null || echo 'Waylaecho "Pi fix done — log out and back in on Pi, then reconnect NoMachine"
[sudo] password for hadi: 
[Desktop]
Session=ubuntu-xorg
NX> 162 Disabled service: nxd.
NX> 162 Disabled service: nxserver.
NX> 162 Disabled service: nxnode.
NX> 111 New connections to NoMachine server are enabled.
NX> 161 Enabled service: nxserver.
NX> 161 Enabled service: nxnode.
NX> 161 Enabled service: nxd.
Pi fix done — log out and back in on Pi, then reconnect NoMachine
(venv) hadi@hadi-desktop:~/Downloads$ export GATE_API_URL="https://automated-gate-access.vercel.app/api"
export GATE_DEVICE_TOKEN="fyp_gate_secret-2026"

(venv) hadi@hadi-desktop:~/Downloads$ 
python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5
python: can't open file '/home/hadi/Downloads/gate_sync.py': [Errno 2] No such file or directory
(venv) hadi@hadi-desktop:~/Downloads$ python gate_sync.py --folder recordings/car_photos/ --preprocess none --delay 5

python: can't open file '/home/hadi/Downloads/gate_sync.py': [Errno 2] No such file or directory
(venv) hadi@hadi-desktop:~/Downloads$ 

python gate_sync.py --video recordings/car_photos/myvideo.mp4 --every 1 --max-frames 5 --preprocess none --delay 5
python: can't open file '/home/hadi/Downloads/gate_sync.py': [Errno 2] No such file or directory
(venv) hadi@hadi-desktop:~/Downloads$
