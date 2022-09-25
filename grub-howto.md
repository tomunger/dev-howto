# General troubleshooting

For [ubuntu](https://help.ubuntu.com/community/Grub2/Troubleshooting).  

With details of the following commands:


from [stackexchange](https://unix.stackexchange.com/questions/418401/grub-error-you-need-to-load-kernel-first)

    set prefix=(hd0,gpt2)/boot/grub
    set root=(hd0,gpt2)
    insmod normal
    normal 

That may bring up the menu.  If not:

    insmod linux
    linux (hd0,gpt2)/boot/vmlinuz root=/dev/sda2
    initrd /initrd.img
    boot 

But maybe if the root is right:

    insmod linux
    linux /vmlinuz root=/dev/sda2
    initrd /initrd.img
    boot 

# Edit grub configuration

See [ubuntu documentation](https://help.ubuntu.com/community/Grub2/Setup)

Default settings in `/etc/default/grub`

It appears two commands are needed:

    sudo update-grub
    sudo grub-install /dev/sdX

