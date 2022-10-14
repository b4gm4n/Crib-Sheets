# Install XRDP

sudo apt install xrdp
(Works on Ubuntu server20.04??, Pi)
sudo reboot

Check running
sudo systemctl status xrdp

not sure if needed check in next install

sudo apt install xfce4 xfce4-goodies xorg dbus-x11 x11-xserver-utils
sudo adduser xrdp ssl-cert

## Firewall  

`sudo apt install ufw` Uncomplicated Firewall  
access from local network  
`sudo ufw allow from 192.168.1.0/24` to any port  
3389 Access from anywhere `sudo ufw allow 3389`  
`sudo ufw enable`  

## Look into XtoGO  

## Vim

[devhints.io/vim](https://devhints.io/vim)  
[vim.rtoor.com](https://vim.rtorr.com/)  
[christitus vim guide](https://christitus.com/vim-the-ultimate-editor/)  

at the command prompt try typing `vimtutor`  
