---
layout: default 
title:  "Octoprint Notes"
parent: 3D Printing
---

### Getting Started
1. download raspbian buster, use etcher or raspbian image to write on ssd
2. setup headless raspberry pi on the newly written sd card: 
    - add wpa_supplicant.conf to boot\ folder
    
```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=<Insert country code here>

network={
 ssid="<Name of your WiFi>"
 psk="<Password for your WiFi>"
}
```
    - add ssh file to boot/  enable ssh
    - change to the same network as your raspberry pi. disable vpn
3. ssh pi@raspberrypi.local 
4. sudo raspi-config: change password, change hostname 
   sudo reboot
5. sudo adduser $username
   - lpass the setup
   - cat /etc/passwd | grep "$username"
   - sudo userdel $username # if problem
   - su - $username # test out the new username
   - sudo usermod -a -G adm,dialout,cdrom,sudo,audio,video,plugdev,games,users,input,netdev,gpio,i2c,spi $username
   - sudo adduser $username sudo # add to sudoer file
   - sudo reboot
   - sudo pkill -u pi; # should not give any response
   - sudo deluser -remove-home pi
   - 
6. sudo apt-get install git
### Ansible 
### Plugins  
