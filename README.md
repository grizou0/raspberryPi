
# raspberryPi  
# Raspberry Pi 4 64 bit   
Apres l'installation de l'os raspbian, on fait un upgrade:    
rpi-update    

sudo nano /boot/config.txt    
on ajoute en fin de fichier:    

# Overclock   
sudo nano /boot/config.txt    
On ajoute:    
over_voltage=6    
arm_freq=2000   
arm_gpu=750   

# Edition bashrc    
sudo nano ~/.bashrc   

#installation de ssh (commande console via le port 22)       
sudo apt install openssh-server     
sur la console pc, on accède avec:      
ssh pi/192.168.0.xx     

#Installation de VNC sur raspberry pi 4 ubuntu 20.10

sudo apt-get update     
sudo apt-get upgrade -y     
sudo apt-get install xfce4 xfce4-appfinder xfce4-whiskermenu-plugin xfce4-weather-plugin xfce4-goodies  #GUI interface       
sudo apt-get install tightvncserver   

on modifie le fichier xstartup      
sudo nano ~/.vnc/startup        
#!/bin/sh   
unset SESSION_MANAGER   
unset DBUS_SESSION_BUS_ADDRESS      
xrdb $HOME/.Xresources  
xsetroot -solid grey  
#x-terminal-emulator -geometry 80x24+10+110 -ls -title "$VNCDESKTOP Desktop" &   
#x-window-manager  
#export XKL_XMODMAP_DISABLE=1  
#/etc/X11/Xsession      
startxfce4 &        

----------------------

ensuite on lance > vncserver :1 -geometry 1280x800 -depth 16    
Pour arrêter: > vncserver -kill :1  
Pour changer le passward: >tightvncpasswd   

Pour le lancer en auto boot:(en essai, non fonctionnel sur ubuntu)  

sudo crontab -e 
addition de la ligne:   
@reboot su - pi -c '/usr/bin/tightserver -geometry 1280x720'    

#----------------------------------     
# Installation Usb Stick memory 
Identification ID:      
pi@raspberrypi:~ $  ls -l /dev/disk/by-uuid/  
total 0 
lrwxrwxrwx 1 root root 15 nov 24 22:17 05c2c54d-f13e-4442-bf69-70e99c3d748d -> ../../mmcblk0p2  
lrwxrwxrwx 1 root root 10 nov 25 15:56 69A3-408D -> ../../sda1  
lrwxrwxrwx 1 root root 15 nov 24 22:17 997C-A34A -> ../../mmcblk0p1 

Auto mount au démarrage du raspberry: 
------------------------------------
sudo nano /etc/fstab  
Addition en fin de ligne  
UUID=69A3-408D /media/usb vfat auto,nofail,noatime,users,rw,uid=pi,gid=pi 0 0   




