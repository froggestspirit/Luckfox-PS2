# Luckfox-PS2
Preconfigured image for Luckfox boards for OPL

This is a preconfigured build to use the Luckfox Pico Plus (no soldering), or the Luckfox Pico Mini B (soldering required) to play backups on PS2 with OPL.

* Follow the instructions here to flash the update.img (Flash this to Nand, not SD card) https://wiki.luckfox.com/Luckfox-Pico/Linux-MacOS-Burn-Image

* The SD card will need to have the standard layout on the root (DVD, etc).

* If building from source, this utilizes the buildroot build, and the overlay files can be copied in after configuring, and running buildrootconfig. A guide for that is beyond the scope of this

* OPL will need to be configured with the following (shoutout to amirzaim and their thread here https://www.psx-place.com/threads/opl-smb-linux-configuration-guide.20638/):

```
-PS2-
IP type : Static
IP  : 192.168.1.10
Netmask :  255.255.255.0
Gateway : 192.168.1.1
DNS Server : 192.168.1.1

-SMB Server-
Address type : IP
Address : 192.168.1.2
Port : 445
Share : PS2SMB
User:
Password:
```

If soldering, you'll need to connect the TX+, TX-, RX+, and RX- wires to the Luckfox board

You can still access the board by connecting it to the computer through USB, and running "sdb shell", but that's only if you want to change some settings on it

Changes:
* /etc/samba/smb.conf (for the samba configuration)
* /etc/init.d/S91smb (to assign a static IP and set up ethernet on boot)
* /etc/init.d/S50usbdevice (disable the RNDIS connection, we don't need it here)

Disclaimers:
* I'm not responsible for any damage done
* I don't condone piracy, only use your legally obtained backups