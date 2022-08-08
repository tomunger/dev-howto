# How to share

[Insructions](https://raspberrypihq.com/how-to-share-a-folder-with-a-windows-computer-from-a-raspberry-pi/)


	sudo apt-get install samba samba-common-bin

Edit conf

	sudo nano /etc/samba/smb.conf
		workgroup = WORKGROUP
		wins support = yes

Edit the [homes] section.  May it read-write and more generous permissions.

