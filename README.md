cd ~/Downloads
rm -f nomachine.deb
file nomachine.deb 2>/dev/null || echo "removed"



cd ~/Downloads
wget --content-disposition "https://www.nomachine.com/free/arm/v8/deb" -O nomachine.deb
file nomachine.deb
ls -lh nomachine.deb
(venv) hadi@hadi-desktop:~/Downloads$ sudo /usr/NX/bin/nxserver --status
sudo: /usr/NX/bin/nxserver: command not found
(venv) hadi@hadi-desktop:~/Downloads$ cd ~/Downloads
rm -f nomachine.deb
file nomachine.deb 2>/dev/null || echo "removed"
nomachine.deb: cannot open `nomachine.deb' (No such file or directory)
(venv) hadi@hadi-desktop:~/Downloads$ cd ~/Downloads
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
(venv) hadi@hadi-desktop:~/Downloads$ 

