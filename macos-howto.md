# MacOS HowTo

## Terminal Environment.

`.profile`

`.zprofile`

`.zshrc`

`.bash_profile`


## zsh

Commands are first read from /etc/zshenv; this cannot be overridden. Subsequent behaviour is modified by the RCS and GLOBAL_RCS options; the former affects all startup files, while the second only affects global startup files (those shown here with an path starting with a /). If one of the options is unset at any point, any subsequent startup file(s) of the corresponding type will not be read. It is also possible for a file in $ZDOTDIR to re-enable GLOBAL_RCS. Both RCS and GLOBAL_RCS are set by default.

Commands are then read from $ZDOTDIR/.zshenv. If the shell is a login shell, commands are read from /etc/zprofile and then $ZDOTDIR/.zprofile. Then, if the shell is interactive, commands are read from /etc/zshrc and then $ZDOTDIR/.zshrc. Finally, if the shell is a login shell, /etc/zlogin and $ZDOTDIR/.zlogin are read.

## Rosetta

`arch` will tell the architecture.

`arch -x86_64 zsh` will run x86 emulation

## HomeBrew

install from [brew.sh].  

Installed in `/opt/homebrew`



## Useful Commands

    brew list            # what is installed.
    brew update            # update homebrew
    brew outdated        # list outdated packages
    brew upgrade        # upgrade all formulae
    brew cleanup        # remove old versions
    brew doctor            # check for problems

Periodic update:

    brew update
    brew upgrade

## Useful Packages

* menumeters - system activity in the menu


## Python

### pyenv

Instructions on [github](https://github.com/pyenv/pyenv)

Installed via github checkout.

Follow instructions to set up `.zprofile` and `.zshrc`

Also install pyenv-virtualenv from [github](https://github.com/pyenv/pyenv-virtualenv)

#### Compiling

Configure the [build environment](https://github.com/pyenv/pyenv/wiki#suggested-build-environment)

Details in pyenv [common build problems](https://github.com/pyenv/pyenv/wiki/Common-build-problems#error-the-python-ssl-extension-was-not-compiled-missing-the-openssl-lib)

`lmza` is in package `xz`.  If build reports that library is not found, try

 * Reinstall `xz`
 * Put `/opt/homebrew/bin` on the path

Current pyenv seems to find libraries as needed.  Old method was to add flags identifying the
library locations:

    export LDFLAGS="-L/opt/homebrew/opt/zlib/lib -L/opt/homebrew/opt/tcl-tk/lib"
    export CPPFLAGS="-I/opt/homebrew/opt/zlib/include -I/opt/homebrew/opt/tcl-tk/include"

HOWEVER, latest pyenv may be able to find these automatically.

Build Python again.

### pandas

Does not build.  TowardDataScience [tried to set it up](https://towardsdatascience.com/new-m1-who-dis-677e085baffd)

Can try using [miniforge](https://github.com/conda-forge/miniforge), which can be installed with brew:

    brew install --cask miniforge
    conda create -n myenv python=3.8
    conda init zsh
    conda activate
    conda install pandas


## Git, GitHub, and GitLab

### Security

See github's [security documentation](https://docs.github.com/en/authentication)


Add SSH key pairs to local agent

    unger@most .ssh % ssh-add
    Identity added: /Users/unger/.ssh/id_ed25519 (tk110@tumtum.com)
    unger@most .ssh % ssh-add -L
    ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIHwpwRYXTqqM2aiTF+RurnRKeTbD144JpuSKL++lQNY+ tk110@tumtum.com
    unger@most .ssh % ls
    #config#        config          id_ed25519      id_ed25519.pub  known_hosts     known_hosts.old
    unger@most .ssh % ssh-add -d id_ed25519      
    Identity removed: id_ed25519 ED25519 (Mist)

