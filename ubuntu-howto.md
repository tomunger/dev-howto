# Microsoft Remote

Install `xrdp`

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



