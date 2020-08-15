#Raspberry Pi Server 1.1

### Random Function Test
```
raspistill -o /home/pi/Dev/camera_dev/images/image_001.jpg
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
    
sudo apt install openssh-server

sudo nano /etc/ssh/sshd_config
    --> AllowUsers username

```

### Get Started
```
git clone  https://github.com/zwerb/rasp_server.git rasp_server
```

### Start A New REpo
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

















 
