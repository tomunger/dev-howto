# Learning

[Chicago Python](https://www.chipy.org)


# Cheat Sheets

[typing](https://mypy.readthedocs.io/en/latest/cheat_sheet_py3.html)


# Python Version Management

## pyenv

RealPython [instructions](https://realpython.com/intro-to-pyenv/).  Explains how to install.

See `.pyenv/README.md` for details on how to set up your shell

Update with

    cd $(pyenv root)
    git pull

### pyenv-virtualenv

See the github [repository](https://github.com/pyenv/pyenv-virtualenv)



### Commands

    # List local versions
    pyenv versions

    # List available verions
    pyenv install --list

    # Install CPythong version
    pyenv install 3.9.7

    



# Tools

Vulnerability testing:  Python safety checks?  Does this exist?

# mypy

Install the mypy VS Code extension

Instructions in that extension tell you to install the language server:

    $ python -m venv ~/.mypyls
    $ ~/.mypyls/bin/pip install "https://github.com/matangover/mypyls/archive/master.zip#egg=mypyls[default-mypy]"

On Debian, must install python3-dev

    sudo apt install python3-dev

# VS Code

Setting `python.analysis.extraPaths` tells pylance where to look for source code.
