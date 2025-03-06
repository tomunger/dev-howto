<!-- markdownlint-disable MD001 MD009 -->
# Raspbian Setup

## Write image on mac

How to write [image on mac](https://www.raspberrypi.org/documentation/installation/installing-images/mac.md)

    diskutil list
    diskutil unmountDisk /dev/disk3
    sudo dd bs=1m if=~/a/2019-04-11-rpd-x86-stretch.iso of=/dev/rdisk3 conv=sync

Alternately, use Etcher application  
to write the OS to a SD card.

## Backup existing on Mac

This [article](https://medium.com/@ccarnino/backup-raspberry-pi-sd-card-on-macos-the-2019-simple-way-to-clone-1517af972ca5) recommends using disk utility to read and Etcher to restore.  Rename extension `cdr` to `iso`.

## Periodic Update

See <https://www.raspberrypi.org/documentation/raspbian/updating.md>

    sudo apt-get update
    sodo apt-get -y upgrade
    sudo apt install --upgrade python3-setuptools

But some packages are held back due to staged releases and dependencies.  These can be updated using the 
desktop tools.

## Auto Login

If you don't already have a key:

    ssh-keygen

leave file name and pass phrase blank.  Then

    ssh-copy-id userid@hostname

## Raspberry settings

From the command line

    sudo raspi-config   

## Disable IP V 6

Sometimes IP V6 does not work.  See [instructions](https://www.howtoraspberry.com/2020/04/disable-ipv6-on-raspberry-pi/)

Insert

    net.ipv6.conf.all.disable_ipv6 = 1
    net.ipv6.conf.default.disable_ipv6 = 1
    net.ipv6.conf.lo.disable_ipv6 = 1

Into `/etc/sysctl.d/50-disableipv6.conf`

## 1Password

Install the browser extension.

Alternately, you can install the application for [ARM architecture](https://support.1password.com/install-linux/#other-distributions-or-arm-targz).

**To install using a .deb file:**

To install a .deb package on a Raspberry Pi, use the command `sudo dpkg -i <package_name.deb>` in the terminal. You may need to run apt -f install afterwards to resolve any dependency issues that might arise.

## Hardware

### Mouse

Slow mouse.  Add this to `/boot/cmdline.txt` (end of line)

    usbhid.mousepoll=0

### Flip mouse wheel

October 2024 raspberry switched to [Wayland](https://www.mankier.com/package/labwc).  This is configured via [labwc](https://www.mankier.com/5/labwc-config).





### /boot/config.txt settings

Settings

[RPI documentation](https://www.raspberrypi.org/documentation/configuration/config-txt/README.md)

Touchscreen display:  see [HowTo-TouchScreenDisplay.md](HowTo-TouchScreenDisplay.md)



## User

Default user is `pi`.  Password for this user is set at configuration.  I use `pi` but the default is `raspberry`.


### GIT configuration

Configure GIT user information with

    git config --global user.name "Tom Unger"
    git config --global user.email "tk110@tumtum.com"

Must be done before using GIT.

## Package Tools

List files in package:

    dpkg -L package

List installed packages

    sudo apt list --installed

## Python

### CircuitPython

Circuit Python is used for the pressure sensor.  See on-line install notes.


## Install support for exFAT file system

    sudo apt-get install exfat-fuse exfat-utils



## Install MS Remote Desktop

You can install Remote Desktop:  [Instructions](https://www.datenreise.de/en/raspberry-pi-install-remote-desktop-xrdp/)

### Commands used:

    sudo apt-get purge realvnc-vnc-server
    sudo apt-get install xrdp

Note:  the XRDP settings in the files `/etc/xrdp/xrdp.ini` and `/etc/xrdp/sesman.ini` can still be adjusted. 

But raspbian comes with VNC and that can be used.  However, headless, the VNC ends up with a small display.  `vncserver` can be used to create virtual screens (1 on port 5001, 2 on port 5002, etc)



## Mount Lita

This did not work on raspbian stretch.

    mount -t cifs //lita.local/home /mnt/home -o user=unger

## GPIO pins

Stackoverflow [discussion](https://stackoverflow.com/questions/30938991/access-gpio-sys-class-gpio-as-non-root)
