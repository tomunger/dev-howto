# How to manage IP address

# DHCP

[dhclient](https://www.computerhope.com/issues/ch001078.htm)

	sudo dhclient -v

Stop server:

	sudo dhclient -v -r

Start server

	sudo dhcplient


# static address

[ifconfig](https://www.computerhope.com/unix/uifconfi.htm)

Bring up or down

	sudo ifconfig eth1 up

Configure

	sudo ifconfig wlan0 69.72.169.1
	sudo ifconfig eth1 netmask 255.255.255.0
	sudo ifconfig eth0 192.168.2.5 netmask 255.255.255.0 broadcast 192.168.2.7


Delete static with one of these:

	sudo ifconfig en1 0.0.0.0
	sudo ifconfig en1 delete 192.168.141.99
	sudo ifconfig en1 del 192.168.141.99

	

