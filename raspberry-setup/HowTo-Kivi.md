# Kivi:  

Raspberry Pi OS Bookworm [ganeral install](https://kivy.org/doc/stable/gettingstarted/installation.html#install-pip) 
and [RPi specific](https://kivy.org/doc/stable/installation/installation-rpi.html)

In summary:

 1. Maybe: Install dependencies.
 2. [`pip` install](https://kivy.org/doc/stable/gettingstarted/installation.html#setup-terminal-and-pip) of kivi
 3. Configure [input](https://kivy.org/doc/stable/installation/installation-rpi.html#using-official-rpi-touch-display) 

Old install on Buster:

[Updated Install](https://github.com/Lauszus/kivy/blob/45f7ec3851e09220b2b5dc8f34523d6eebff17c2/doc/sources/installation/installation-rpi.rst) for Pi 4 and Buster
(github [issue](https://github.com/kivy/kivy/issues/6474) on difficulties with Buster).


## Touch Input

From https://www.raspberrypi.org/forums/viewtopic.php?f=108&t=121378

in ~/.kivy/config.ini make the input section:

[input]
mouse = mouse
mtdev_%(name)s = probesysfs,provider=mtdev
hid_%(name)s = probesysfs,provider=hidinput

If the line:

    ; %(name)s = probesysfs

is present, that will generate a duplicate event for every touch.  Comment that line out
