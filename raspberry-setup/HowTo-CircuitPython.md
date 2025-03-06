<!-- markdownlint-disable MD001 MD009 -->
# Install

Instructions from [AdaFruit](https://learn.adafruit.com/circuitpython-on-raspberrypi-linux/installing-circuitpython-on-raspberry-pi)

CircuitPython is based on Python and designed to run on small boards. It can be run on 
single board computers (Raspberry) using [Blinka](https://circuitpython.org/blinka)

Create a virtual environment with system site packages

    python3 -m venv env --system-site-packages

Basic commands for installing in a virtual environment.

    pip3 install --upgrade adafruit-python-shell
    wget https://raw.githubusercontent.com/adafruit/Raspberry-Pi-Installer-Scripts/master/raspi-blinka.py
    sudo -E env PATH=$PATH python3 raspi-blinka.py

There are further details on how to do a manual install.

## Pressure sensor

Requires install of the mprls library:

    pip3 install adafruit-circuitpython-mprls
