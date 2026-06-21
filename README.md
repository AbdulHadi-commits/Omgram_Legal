venv) hadi@hadi-desktop:~/Downloads$ cd ~/Downloads
wget --content-disposition "https://www.nomachine.com/free/arm/v8/deb" -O nomachine.deb
file nomachine.deb
ls -lh nomachine.deb
--2026-06-21 16:19:55--  https://www.nomachine.com/free/arm/v8/deb
Resolving www.nomachine.com (www.nomachine.com)... 80.92.83.99
Connecting to www.nomachine.com (www.nomachine.com)|80.92.83.99|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://download.nomachine.com/download/9.7/Raspberry/nomachine_9.7.3_1_arm64.deb [following]
--2026-06-21 16:19:57--  https://download.nomachine.com/download/9.7/Raspberry/nomachine_9.7.3_1_arm64.deb
Resolving download.nomachine.com (download.nomachine.com)... 80.92.89.79
Connecting to download.nomachine.com (download.nomachine.com)|80.92.89.79|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://web9001.nomachine.com/download/9.7/Raspberry/nomachine_9.7.3_1_arm64.deb [following]
--2026-06-21 16:19:58--  https://web9001.nomachine.com/download/9.7/Raspberry/nomachine_9.7.3_1_arm64.deb
Resolving web9001.nomachine.com (web9001.nomachine.com)... 83.222.232.25
Connecting to web9001.nomachine.com (web9001.nomachine.com)|83.222.232.25|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 77721282 (74M) [application/octet-stream]
Saving to: ‘nomachine.deb’

nomachine.deb       100%[==================>]  74.12M   380KB/s    in 3m 12s  

2026-06-21 16:23:12 (395 KB/s) - ‘nomachine.deb’ saved [77721282/77721282]

nomachine.deb: Debian binary package (format 2.0), with control.tar.gz , data compression xz
-rw-rw-r-- 1 hadi hadi 75M Jun 15 13:59 nomachine.deb
(venv) hadi@hadi-desktop:~/Downloads$ cd ~/Downloads
sudo dpkg -i nomachine.deb
sudo apt-get install -f -y
Selecting previously unselected package nomachine.
(Reading database ... 124765 files and directories currently installed.)
Preparing to unpack nomachine.deb ...
Unpacking nomachine (9.7.3-1) ...
Setting up nomachine (9.7.3-1) ...
NX> 700 Starting installation at: Sun, 21 Jun 2026 16:26:57.
NX> 700 Using installation profile: Ubuntu.
NX> 700 Installation log is: /usr/NX/var/log/install.log.
NX> 700 Installing nxrunner version: 9.7.3.
NX> 700 Installing nxplayer version: 9.7.3.
NX> 700 Installing nxnode version: 9.7.3.
NX> 700 Installing nxserver version: 9.7.3.
NX> 700 Installation completed at: Sun, 21 Jun 2026 16:27:18.
NX> 700 NoMachine was configured to run the following services:
NX> 700 NX service on port: 4000
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cloud-guest-utils eatmydata gdisk libeatmydata1 libfile-fnmatch-perl
  libgl1-amber-dri libglapi-mesa libllvm17t64 libllvm19 libxcb-dri2-0
  python-babel-localedata python3-attr python3-babel python3-configobj
  python3-jinja2 python3-json-pointer python3-jsonpatch python3-jsonschema
  python3-pyrsistent python3-serial python3-tz
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 528 not upgraded.
(venv) hadi@hadi-desktop:~/Downloads$ sudo /usr/NX/bin/nxserver --status
NX> 111 New connections to NoMachine server are enabled.
NX> 161 Enabled service: nxserver.
NX> 161 Enabled service: nxnode.
NX> 161 Enabled service: nxd.
(venv) hadi@hadi-desktop:~/Downloads$ 

