# raspberryPi
command générale  
# Installation Usb Stick memory
Identification ID:  
pi@raspberrypi:~ $  ls -l /dev/disk/by-uuid/  
total 0 
lrwxrwxrwx 1 root root 15 nov 24 22:17 05c2c54d-f13e-4442-bf69-70e99c3d748d -> ../../mmcblk0p2  
lrwxrwxrwx 1 root root 10 nov 25 15:56 69A3-408D -> ../../sda1  
lrwxrwxrwx 1 root root 15 nov 24 22:17 997C-A34A -> ../../mmcblk0p1 
Creation un "mount point" :
--------------------------  

sudo mkdir /media/usb 
sudo chown -R pi:pi /media/usb  
sudo mount /dev/sda1 /media/usb -o uid=pi,gid=pi
umount /media/usb
Auto mount au démarrage di raspberry: 
------------------------------------

sudo nano /etc/fstab
UUID=18A9-9943 /media/usb vfat auto,nofail,noatime,users,rw,uid=pi,gid=pi 0 0



