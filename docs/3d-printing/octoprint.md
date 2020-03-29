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
4. sudo raspi-config:
   	- change password,
	- change hostname ,
	- enlarge filesystem to use up all that sd card
	- enable perip, camera enable
   sudo reboot
5. sudo adduser $username
   - lpass the setup
   - cat /etc/passwd | grep "$username"
   - sudo userdel $username # if problem
   - su - $username # test out the new username
   - sudo adduser $username sudo # add to sudoer file
   - sudo usermod -a -G adm,dialout,cdrom,sudo,audio,video,plugdev,games,users,input,netdev,gpio,i2c,spi $username
   # access to various perips for raspberry pi 
   - sudo reboot
   - sudo pkill -u pi; # should not give any response
   - sudo deluser -remove-home pi
   - follow stuff that make sense at https://www.raspberrypi.org/documentation/configuration/security.md
7. get mjpg-streamer
8. octoprint local build 2.7 ( OMG why is it not Python3 yet) 
    - pip : default install not on PATH  https://pip.pypa.io/en/latest/installing/
    - pip install virtualenv
    - cd /home/$username ; virtualenv OctoPrintPY27

8.1 octoprint local build 3.
    - sudo apt install python3-pip
    - update profile to have pip/virtual clearly distinguish between 2 and 3
    - user must have dialout unix group for connecting to ttyACM0 usb port
    -
9. Octoprint Printing
  - Don't save to SD card : computer- network-raspbi - serial(one line ack/ at time slow)  ->prusa marlin

10. openssh server on your computer
    - allow specific port for ssh by edit Port on  etc/ssh/sshd-config
    - configure octo to have specific port for connecting to your server ~/.ssh/config
    - rsync command : rsync -rvz --progress ./cam.jpg  $username@$castle:Downloads/cam.jpg
    
6. sudo apt-get install git
### Ansible 
### Plugins  
