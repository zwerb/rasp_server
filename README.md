#Raspberry Pi Server 1.1

This is my how to for setting up and running a raspberry pi server on your home network.

**TO DO**: Still need to organize this from step one

## Step 0 (TBD): Install Hardware and OS on a Raspi-4 https://projects.raspberrypi.org/en/projects/raspberry-pi-setting-up 

## Step 1 SSH Access 

### Setup SSH on the Pi
```
sudo apt install openssh-server

sudo nano /etc/ssh/sshd_config
    --> AllowUsers username
    
sudo systemctl enable ssh
sudo systemctl start ssh

hostname -I
```

### Securing the Pi
```
sudo adduser username
sudo usermod -a -G adm,dialout,cdrom,sudo,audio,video,plugdev,games,users,input,netdev,gpio,i2c,spi username
sudo su - usernamne

sudo raspi-config
    --> change boot options to desktop with user login (instead of default autologin)
    
sudo pkill -u pi
sudo deluser pi
sudo deluser -remove-home pi

sudo visudo /etc/sudoers.d/010_pi-nopasswd
    --> pi ALL=(ALL) NOPASSWD: ALL --> pi ALL=(ALL) PASSWD: ALL
    :q
```


## Step 2 - Set up a Git for Coding Projects

### Get Started
```
git clone  https://github.com/zwerb/rasp_server.git rasp_server
```

### Start A New Repo
```
echo "# rasp_server" >> README.md
git init
git add README.md
ls -al
git commit -m "first commit"
git remote add origin https://github.com/zwerb/rasp_server.git
git push -u origin master
```

### Add New
```
git remote add origin https://github.com/zwerb/rasp_server.git
git push -u origin master
```

### Update and Config
```
sudo apt update
sudo apt full-upgradesudo 

sudo raspi-config
```

## Logging In

### Client SSH:
```
ssh pi@ip.ip.ip.ip
```

### Get to Dev:
```
cd /home/pi/Dev/
```

## Step 3 - Camera Functions

### Setup Camera on Pi
```
sudo raspi-config
    4 --> Camera --> Enable
```


### Run Camera Functions Test
```
raspistill -rot 90 -o /home/pi/Dev/camera_dev/images/image_001.jpg

cd /home/pi/Dev/camera_dev
./camerashot.sh

display images/image_ [TAB]

```

### Set up Camera Functions Test Bash
```
cd /home/pi/Dev/camera_dev/

touch camerashot.sh

#!/bin/bash
DATE=$(date +"%Y-%m-%d_%H%M")
raspistill -rot 90 -o /home/pi/Dev/camera_dev/images/$DATE.jpg -w 800 -h 600

^o
^x

chmod +x camerashot.sh

./camerashot.sh
```













 
