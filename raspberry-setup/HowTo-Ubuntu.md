# Ubuntu Server

## GPIO Access

	sudo apt-get install python3-venv
	sudo apt-get install python3-dev
	sudo apt install gcc
	python3 -m venv env
	. env/bin/activate
	pip install wheel
	pip install RPi.GPIO

Change permissions on GPIO device.  Default user, `ubuntu` is in `dialup` group so we need to make
the device accessible by that group.  I read this on the internet.  Seems to be the standard.

	sudo chgrp dialout /dev/gpiomem
	sudo chmod g+rw /dev/gpiomem

Lists groups the current user belongs to.

	groups

## Display Access

todo