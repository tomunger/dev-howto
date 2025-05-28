# Python HowTo

## Learning

[Chicago Python](https://www.chipy.org) has learning resources


## Cheat Sheets

mypy [typing hints](https://mypy.readthedocs.io/en/latest/cheat_sheet_py3.html)

## Formatting

For a long time I used tabs but the standard is spaces.  I surrender and am switching to spaces
The following command will change all python files to space indentation

    find . -name '*.py' ! -type d -exec bash -c 'expand -t 4 "$0" > /tmp/e && mv /tmp/e "$0"' {} \;



## Python Version Management

### uv

### hatch

Hatch is python packaging authority tool.  

### pyenv

abandoned for `uv` and `hatch`

## Tools

Vulnerability testing:  Python safety checks?  Does this exist?

## mypy

Install the mypy VS Code extension

Instructions in that extension tell you to install the language server:

    $ python -m venv ~/.mypyls
    $ ~/.mypyls/bin/pip install "https://github.com/matangover/mypyls/archive/master.zip#egg=mypyls[default-mypy]"

On Debian, must install python3-dev

    sudo apt install python3-dev

## VS Code

### Hinting and Linting in VS Code

https://devblogs.microsoft.com/python/python-linting-video/?ocid=python_eml_tnp_autoid10_readmore



#### PYTHONPATH

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

## Profiling

[RunSnakeRun](http://www.vrplumber.com/programming/runsnakerun/) provide a GUI that allows you to view (Python) `cProfile` or `Profile` profiler dumps in a sortable GUI view.  

[kcachegrind](https://github.com/KDE/kcachegrind) a KDE GUI display of profilers.

## Message Queue

### MQ Libraries
 
- [kombu](https://docs.celeryq.dev/projects/kombu/en/latest/index.html) provides a high level interface.
- [amqp](https://pypi.org/project/amqp/) Pure python client alternate to librabbitmq.
- [librabbitmq](https://pypi.org/project/librabbitmq/) High performance interface to librabbit.

## Tasks

[Asynchronous Tasks With Django and Celery](https://realpython.com/asynchronous-tasks-with-django-and-celery/)

includes how to use redis and how to use redis as the cellery broker and database back end.  How to use celery with django.

## Frameworks

James Bennett's [asyncio blog post](https://www.b-list.org/weblog/2022/aug/16/async/) (8/2022) lists several frameworks.

## Libraries

### attrs

[Attrs module](https://www.attrs.org/en/stable/) provides much of the class writing boiler plate.  Lighter
than pydantic, which is data validation.


### pydantic

[Pydantic module](https://pydantic-docs.helpmanual.io/) "provides data validation and settings management using pythong type annotations."

### Database

Python as a DB API specification in [PEP249](https://peps.python.org/pep-0249/).  As I understand, database drives implement this interface and provide the interface to various database servers.  This is a low level interface.  In theory, I think, you can change database by importing a different DBAPI driver.

[Sql Server](https://docs.microsoft.com/en-us/sql/connect/python/pyodbc/python-sql-driver-pyodbc?view=sql-server-ver16) `pyodbc` is the driver for MS SQL Server and other ODBC.  Source on [GitHub](https://github.com/mkleehammer/pyodbc)

[aiodbc](https://github.com/aio-libs/aioodbc) is an async ODBC driver that uses `pyodbc` and creates threads to manage async.

On top of DBAPI drivers, several higher level frameworks provide a more abstract database interface.

[SQLAlchemy](https://www.sqlalchemy.org/) - generally what people use for DB /ORM.

[Databases Project](https://www.encode.io/databases/) Databases gives you simple asyncio support for a range of databases.  It allows you to make queries using the powerful SQLAlchemy Core expression language, and provides support for PostgreSQL, MySQL, and SQLite.

[SQLModel](https://sqlmodel.tiangolo.com/) SQLModel, SQL databases in Python, designed for simplicity, compatibility, and robustness. Powered by Pydanic and SQLSlchemy.  Designe to simplify interacting with SQL database in FastAPI.

*Why choose SQL Model over SQLAlchemy?*

### Requests

The [requests](https://requests.readthedocs.io/en/latest/) is the standard for making HTTP requests.  Requests recommends several packages:

- [CacheControl](https://cachecontrol.readthedocs.io/en/latest/) caching
- [Requests-Threads](https://github.com/requests/requests-threads) is a Requests session that returns the amazing Twisted’s awaitable Deferreds instead of Response objects. This allows the use of async/await keyword usage on Python 3, or Twisted’s style of programming, if desired.
- [Requests-Toolbelt](https://github.com/requests/requests-threads) is a collection of utilities that some users of Requests may desire, but do not belong in Requests proper. 
- [requests-oauthlib](https://requests-oauthlib.readthedocs.io/en/latest/) makes it possible to do the OAuth dance from Requests automatically. This is useful for the large number of websites that use OAuth to provide authentication. It also provides a lot of tweaks that handle ways that specific OAuth providers differ from the standard specifications.

- Certifi is a carefully curated collection of Root Certificates for validating the trustworthiness of SSL certificates while verifying the identity of TLS hosts. It has been extracted from the Requests project.

[HTTPX](https://www.python-httpx.org/) HTTPX is a fully featured HTTP client for Python 3, which provides sync and async APIs, and support for both HTTP/1.1 and HTTP/2.  Mostly a drop in replacement for requests.

### Caching general

[dogpile](https://dogpilecache.sqlalchemy.org/en/latest/) provide threaded caching, including managing updates.

### Web frameworks

Django

Flask

[Shiny for Python](https://shiny.posit.co/py/) Interactive web applications.

[nicegui](http://nicegui.io/) Web interface to your application.

### Web Servers

A web framework needs to be run by a web server:

[Gunicorn](https://gunicorn.org/) a WSGI HTTP server for unix.  

ASGI server implementations, like [Daphne](https://github.com/django/daphne), [Hypercorn](https://gitlab.com/pgjones/hypercorn/), and [Uvicorn](https://www.uvicorn.org/).

### API

[Starlette](https://www.starlette.io/) Starlette is a lightweight ASGI framework/toolkit, which is ideal for building async web services in Python.

[FastAPI](https://fastapi.tiangolo.com/) is the web framework that seems to have the most interest/noise around it.

[LightStar](https://github.com/litestar-org/litestar) API framework.  Featured on Talk Python to Me.

[msgpack](https://pypi.org/project/msgpack/) fast message serialization.  Used by LightStar.

