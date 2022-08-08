# How to install VS Code

[code.headmelted.com](https://code.headmelted.com)
[headmelted github](https://github.com/headmelted)

Currently latest version does not run on RPI.  This [github issue discusses](https://github.com/headmelted/codebuilds/issues/79)


## Install

Declare repository.

	curl -s https://packagecloud.io/install/repositories/headmelted/codebuilds/script.deb.sh | sudo bash

Install code-oss

	curl -L https://code.headmelted.com/installers/apt.sh | sudo bash

(alt `. <( wget -O - https://code.headmelted.com/installers/apt.sh )`)


## Downgrade to version 1.29 (8/15/2019)

	sudo apt-get purge code-oss
	sudo apt-get install code-oss=1.29.0-1539702286
	sudo apt-mark hold code-oss

