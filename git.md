
# GIT Submodules

GIT [submodule documentation](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

To add a repository as a Submodules

	git submodule add https://github.com/chaconinc/DbConnector

What has changed?

	git diff --cached DbConnector
	git diff --cached --submodule DbConnector

Cloning a repo with submodules does not bring down the submodules.  

	git submodule init
	git submodule update

Or do this when cloning main repo:

	git clone --recurse-submodules https://github.com/chaconinc/MainProject

To pull new changes in the sub-module, go into the directory and `pull` changes.  Or:

	git submodule update --remote DbConnector
