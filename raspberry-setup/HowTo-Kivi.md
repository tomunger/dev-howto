# Kivi:  

[OLD Installation](http://kivy.org/docs/installation/installation-rpi.html)

[Updated Install](https://github.com/Lauszus/kivy/blob/45f7ec3851e09220b2b5dc8f34523d6eebff17c2/doc/sources/installation/installation-rpi.rst) for Pi 4 and Buster
(github [issue](https://github.com/kivy/kivy/issues/6474) on difficulties with Buster).


## Touch Input

From https://www.raspberrypi.org/forums/viewtopic.php?f=108&t=121378

in ~/.kivy/config.ini make the input section:

[input]
mouse = mouse
mtdev_%(name)s = probesysfs,provider=mtdev
hid_%(name)s = probesysfs,provider=hidinput