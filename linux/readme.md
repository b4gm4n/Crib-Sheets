## Install ZXRDP


sudo apt install xrdp
(Works on Ubuntu server20.04??, Pi)
sudo reboot

Check running
sudo systemctl status xrdp

not sure if needed check in next install

sudo apt install xfce4 xfce4-goodies xorg dbus-x11 x11-xserver-utils
sudo adduser xrdp ssl-cert

Firewall
access from local network
sudo ufw allow from 192.168.1.0/24 to any port 3389
Access from anywhere
sudo ufw allow 3389

### Look into XtoGO