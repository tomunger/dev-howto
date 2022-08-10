# Learning

[Chicago Python](https://www.chipy.org)


# Cheat Sheets

[typing](https://mypy.readthedocs.io/en/latest/cheat_sheet_py3.html)

# formatting

For a long time I used tabs but the standard is spaces.  I surrender and am switching to spaces
The following command will change all python files to space indentation

    find . -name '*.py' ! -type d -exec bash -c 'expand -t 4 "$0" > /tmp/e && mv /tmp/e "$0"' {} \;



# Python Version Management

## pyenv

`pyenv` has become my favored way to manage python on my personal computer and development systems.
A little complex to set up, it then makes it easy to create, re-create, and swith environments.

RealPython [instructions](https://realpython.com/intro-to-pyenv/).  Explains how to install.

See `.pyenv/README.md` for details on how to set up your shell

Update with

    cd $(pyenv root)
    git pull

### pyenv-virtualenv

I use this for virtual environtments.

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

## PYTHONPATH

This is more complex that it should be.  I often have one or two library directories that need to be 
available on the path.


`settings.json` will give you the path in terminals.  Since the debugger is run from a terminal, this is where the 
debugger gets the path.

    "terminal.integrated.env.osx": {
        "PYTHONPATH": "${workspaceRoot}/lib"	        
    },
    "terminal.integrated.env.linux": {
        "PYTHONPATH": "${workspaceRoot}/lib"	        
    }

`.env` file.  

    PYTHONPATH=lib


Setting `python.analysis.extraPaths` tells pylance where to look for source code.


# Message Queue

## Libraries
 
 * [kombu](https://docs.celeryq.dev/projects/kombu/en/latest/index.html) provides a high level interface.
 * [amqp](https://pypi.org/project/amqp/) Pure python client alternate to librabbitmq.
 * [librabbitmq](https://pypi.org/project/librabbitmq/) High performance interface to librabbit.


# Tasks

[Asynchronous Tasks With Django and Celery](https://realpython.com/asynchronous-tasks-with-django-and-celery/)

includes how to use redis and how to use redis as the cellery broker and database back end.  How to use celery with django.
