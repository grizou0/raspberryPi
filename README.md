# raspberryPi    
# Installation VNC sur Raspberry Pi Ubuntu 20.10    
A:Solution  (en essai , no fonctionnel )    
    sudo dpkg --add-architecture armhf && sudo apt update   
    sudo apt install libx11-6   
    download RealVNC Server for Raspberry (https://www.realvnc.com/download/file/vnc.files/VNC-Server-6.7.2-Linux-ARM.deb 32) and Install with GDebi  
B:Autre solution via tightvncserver     
sudo apt-get update     
sudo apt-get upgrade -y 
sudo apt-get install tightvncserver 
ensuite on lance > vncserver :1 -geometry 1280x800 -depth 16    
Pour arrêter: > vncserver -kill :1  
Pour changer le passward: >tightvncpasswd   

Pour le lancer en auto boot:(en essai, non fonctionnel sur ubuntu)  

sudo crontab -e 
addition de la ligne:   
@reboot su - pi -c '/usr/bin/tightserver -geometry 1280x720'    



On installe ensuite RealVNC client sur le pc (voir site realvnc)  

Si erreur de connction "Could not acquire name on session bus"  
il faut modifier le fichier sudo nano ~/.vnc/xstartup 
#!/bin/sh 
unset SESSION_MANAGER 
unset DBUS_SESSION_BUS_ADDRESS  
mate-session  
xrdb $HOME/.Xresources  
xsetroot -solid grey  
x-terminal-emulator -geometry 80x24+10+110 -ls -title "$VNCDESKTOP Desktop" & 
x-window-manager  
export XKL_XMODMAP_DISABLE=1  
/etc/X11/Xsession 




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




