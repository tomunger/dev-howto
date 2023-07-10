# Microsoft Remote

As of version 22.04 RDP is the default.  However, the password is differant than the user password and gets reset
on every reboot.  Find the password in Utilities > Passwords and Keys > GNOME Remote Desktop RDP.

Solutions:

 * [Change the keyring password to empty](https://askubuntu.com/questions/1403943/22-04-remote-desktop-sharing-authentication-password-changes-every-reboot)
 * [Manual install of XRDP](https://askubuntu.com/questions/1407444/ubuntu-22-04-remote-desktop-headless).  However, this prevents
simultanenous local and remote log in.
 * At above also the solution of auto-login + run a script tha imports known password to the kiy ring.



## Authentication Required

Solution proposed by [devanswers.co](https://devanswers.co/how-to-fix-authentication-is-required-to-create-a-color-profile-managed-device-on-ubuntu-20-04-20-10/)
and [c-nergy.be](https://c-nergy.be/blog/?p=12073) 

 
    sudo nano /etc/polkit-1/localauthority/50-local.d/45-allow-colord.pkla

paste in

[Allow Colord all Users]
Identity=unix-user:*
Action=org.freedesktop.color-manager.create-device;org.freedesktop.color-manager.create-profile;org.freedesktop.color-manager.delete-device;org.freedesktop.color-manager.delete-profile;org.freedesktop.color-manager.modify-device;org.freedesktop.color-manager.modify-profile
ResultAny=no
ResultInactive=no
ResultActive=yes

For "Update system repositories"

    nano 40-allow-update-repo.pkla

paste in:

[Allow Package Management all Users]
Identity=unix-user:*
Action=org.freedesktop.packagekit.system-sources-refresh
ResultAny=yes
ResultInactive=yes
ResultActive=yes



# Python

Install pyenv and pyenv-virtualenv

Install the recommended [dependencies](https://github.com/pyenv/pyenv/wiki#suggested-build-environment)



# Docker

## Desktop

How to install docker desktop.  There are 

 * Linux general [instructions](https://docs.docker.com/desktop/install/linux-install/)
 * Ubuntu [specific instrucations](https://docs.docker.com/desktop/install/ubuntu/)

1. Setup the [repository](https://docs.docker.com/engine/install/ubuntu/#set-up-the-repository)

    sudo apt-get update
    sudo apt-get install \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
    sudo mkdir -m 0755 -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

2. Download the latest DEB package

3. Install the package (Note the update is necessary to fetch the list of docer packages configured above)
    
    sudo apt-get update
    sudo apt-get install ~/Downloads/docker-desktop-4.17.0-amd64.deb

4. Configure []`pass`](https://docs.docker.com/desktop/get-started/#credentials-management-for-linux-users)

    gpg --generate-key

Now you can run docker


# UFW Firewall

The Uncomplicated Fire Wall

Uncomplicated Fire Wall [tutorial](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands)

    sudo ufw status
    sudo ufw enable
    sudo ufw disable

    sudo ufw allow OpenSSH
    sudo ufw allow 7200/tcp
    sudo ufw allow 9980:9999/tcp