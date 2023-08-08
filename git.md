# How to use GIT

# Set up to contribute to open source

[Rose Judge recommends](https://github.com/readme/guides/configure-git-environment) 
adding an "upstream" remote to track the main repository and a 
branch that has latest main.  Your fork
of that repository does not automatically receive updates from the main.  T

# Squashing commits

Best explained by [W3docs](https://www.w3docs.com/snippets/git/how-to-combine-multiple-commits-into-one-with-3-steps.html)

Rebase to the start of the sequence you want to squash

	git rebase -i HEAD~3

After the first step, the editor window will show up offering you to input the command for each commit. All you need to do is replacing pick with squash, starting from the second line. Then, save the file.

One more editor window will show up to change the resulting commit message. Here, you can find all your commit messages and change them according to your exact needs.

You should run git push to add a new commit to the remote origin. If you have already pushed your commits, then you should force push them using the git push command with --force flag (suppose, the name of remote is origin, which is by default):

	git push --force origin HEAD

or --force-with-lease will not overwrite the work done on the remote branch in case other commits were attached.

	git push --force-with-lease origin HEAD

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


# GITHUB deployment access to repositories

To provide system access to a repository not using personal ssh keys one option is [repository deployment keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/managing-deploy-keys#deploy-keys).

**1** Generate keys for each repository:

	ssh-keygen -t ed25519 -C "IS-SET1 intg-configuration" -f is-set1-github-intg-configuration
	ssh-keygen -t ed25519 -C "IS-SET1 intg-core" -f is-set1-github-intg-core

**2** Create a `config` file mapping a made-up host name to each key:

	Host github.com-intg-configuration
		Hostname github.com
		IdentityFile=/c/Users/Administrator/.ssh/is-set1-github-intg-configuration

	Host github.com-intg-core
		Hostname github.com
		IdentityFile=/c/Users/Administrator/.ssh/is-set1-github-intg-core

**3** Add the deployment keys to the repository.  CHOOSE WRITE ACCESS as needed.

**4** Clone using the made-up host name (or change URL in existing repo):

	# Show remote URL
	git remote -v

	# Change remote URL
	git remote set-url origin git@github.com-intg-configuration:MITEM/intg-configuration.git
	git remote set-url origin git@github.com-intg-core:MITEM/intg-core.git

	# Confirm access
	git remote show origin
