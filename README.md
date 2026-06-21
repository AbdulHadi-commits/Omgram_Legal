NODE_CFG="/usr/NX/etc/node.cfg"
sudo cp -a "$NODE_CFG" "${NODE_CFG}.bak"

sudo sed -i 's/^#\?EnableHardwareEncoding .*/EnableHardwareEncoding 0/' "$NODE_CFG"
grep -q '^EnableHardwareEncoding ' "$NODE_CFG" || echo 'EnableHardwareEncoding 0' | sudo tee -a "$NODE_CFG"

sudo sed -i 's/^#\?EnableDisplayServerVideoCodec .*/EnableDisplayServerVideoCodec 1/' "$NODE_CFG"
grep -q '^EnableDisplayServerVideoCodec ' "$NODE_CFG" || echo 'EnableDisplayServerVideoCodec 1' | sudo tee -a "$NODE_CFG"

sudo sed -i 's/^#\?DisplayServerVideoCodec .*/DisplayServerVideoCodec mjpeg/' "$NODE_CFG"
grep -q '^DisplayServerVideoCodec ' "$NODE_CFG" || echo 'DisplayServerVideoCodec mjpeg' | sudo tee -a "$NODE_CFG"

sudo sed -i 's/#WaylandEnable=false/WaylandEnable=false/' /etc/gdm3/custom.conf 2>/dev/null
grep -q '^WaylandEnable=false' /etc/gdm3/custom.conf 2>/dev/null || echo 'WaylandEnable=false' | sudo tee -a /etc/gdm3/custom.conf 2>/dev/null

echo -e "[Desktop]\nSession=ubuntu-xorg" | sudo tee /home/hadi/.dmrc
sudo chown hadi:hadi /home/hadi/.dmrc

sudo /usr/NX/bin/nxserver --restart
echo "Pi fix done — log out and back in on Pi, then reconnect NoMachine"
