cd ~/Downloads
rm -f nomachine.deb
file nomachine.deb 2>/dev/null || echo "removed"



cd ~/Downloads
wget --content-disposition "https://www.nomachine.com/free/arm/v8/deb" -O nomachine.deb
file nomachine.deb
ls -lh nomachine.deb
