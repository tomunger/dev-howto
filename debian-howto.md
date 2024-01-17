
# Basic Installs

    sudo apt install git


# VS Code

Install using the Ubuntu Software tool.  Or, see [offical instructions](https://code.visualstudio.com/docs/setup/linux) (which are not clear).



# Remote Desktop

Instructions on [how to install xrdp](https://linuxize.com/post/how-to-install-xrdp-on-ubuntu-20-04/)

Install

    sudo apt install xrdp 

Check

    sudo systemctl status xrdp

Set up:  grant xrdp user access to ssl certificates then restart the server

    sudo adduser xrdp ssl-cert
    sudo systemctl restart xrdp
    
Show status

    sudo systemctl status xrdp

# SUDO

The preferred way to grant individual (or group) permissions would be to add files under /etc/sudoers.d

This separates local changes from the default policy and saves time in case the distribution sudoers file changes.

To make the currently logged in user a a sudoer and make sudo not prompt them for a password, use

    echo "$USER ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/$USER
    
this will create a file called /etc/sudoers.d/$USER (where $USER is the username of the user that you were logged in as when you ran that command), making it clear which users are granted permission.



# Docker

Following instructions on [docker](https://docs.docker.com/engine/install/debian/)

Update with:

    sudo apt-get update

Test with:

    sudo docker run hello-world

To try something more ambitious, you can run an Ubuntu container with:

    docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:  [https://hub.docker.com/]

For more examples and ideas, visit: [https://docs.docker.com/get-started/]
 
# CIFS Client

	mount -t cifs //lita.local/home /mnt/home -o user=unger,vers=3.0

Version needs to be supported.  May need to specify


# MariaDB

Instructions at [digitalocean](https://www.digitalocean.com/community/tutorials/how-to-install-mariadb-on-debian-10)

