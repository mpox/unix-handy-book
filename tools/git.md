
# GIT

### Clone and init

Create working copy of repository. <url> might point to local 
path like `/path/to/repository`, or to remote like 
`user@host:/path/to/repository`

	git clone <url>

Create working copy of repository <url> and created dir is 
called <dirname>

	git clone <url> <dirname>

Create new empty working space in a current dir

	git init

Create new sharable origin repository

	git init --bare test_repo.git

Clone only single branch

	git clone -b productionready --single-branch <url>

Clone only single branch to a specified directory name

	git clone -b productionready --single-branch <url> <dirname>

Number of commits

	git rev-list HEAD --count


### Remotes

Which remote servers are configured for the working copy

	git remote -v
	
Details of a remote

	git remote show <remote>
	
	git remote show origin
	
Remove remote reference

	git remote remove <shortname>
	
Add repository from local to remote server

	git remote add <local> <url>
	git remote add origin git@polomagellan.pl:<repo>.git

Przypisanie brancha aktualnie sledzonego

	git branch --set-upstream-to=origin/master master

Push local branch master to remote server origin

	git push origin master

Push local branch master as branch super to remote server origin

	git push origin master:super

Push local branch privdns to repository

	git push -u origin privdns

Delete remote branch

	git push origin --delete serverfix

# Checkout

Create new branch and swtch to it. same as git: branch <name> && git checkout <name>

	git checkout -b branch_name

Create new branch of a certain tag point (version) and swtch to it

	git checkout -b branch_name <tag>

	git checkout -b <branch> <remote>/<branch>

Switch back to master

	git checkout master

Revert file changes to last content in HEAD. changes already added to index and new files will be kept

	git checkout -- <filename/dirname>

Checkout remote branch

	git checkout --track origin/<branch>

Delete given branch

	git branch -d branch_name

Creates new branch, but doesn't switch to it

	git branch branch_name

Listing of your current branches

	git branch

More details

	git branch -v

Branches already merged to current branch

	git branch --merged

Branches not yet merged to current branch

	git branch --no-merged


# Managing files

Used also to mark files as merged

	git add <files>

Stages All

	git add -A 

Stages new and modified, without deleted

	git add . 

Stages modified and deleted, without new

	git add -u 

Remove from stagging area and from working copy (from disk). after commit file will be removed form repository

	git rm <file>

Remove from stagging area, but keep on disk. it's if you added a file by mistake (like log files or something)

	git rm --cached <file>

Rename/move file in git. same as: mv <old> <new> && git rm <old> && git add <new>

	git mv <old name> <new name>

Drop all local changes and commits

	git reset --hard origin/master

Drop file changes (unstage file)

	git reset HEAD <file>

Status 

	git status

Short status

	git status -s

What has benn changed and unstaged

	git diff

What is going to be committed

	git diff --cached

What is staged and going wirh next commit

	git diff --staged

Before merging changes

	git diff <src branch> <target branch>

	git commit -m "<description>"

Opens editor for commit message and puts diff result in that editor

	git commit -v

Does git add on all tracked files before the commit

	git commit -a

This commit replaces results of the previous

	git commit --amend


### Fetch and merge

Get all changes of given project from the server

	git fetch <shortname>

Get all changes of origin at remote server

	git fetch origin

Fetch from all remote servers

	git fetch --all

Fetch and merge remote chnges to local working copy

	git pull

Merge given <branch> to a current branch

	git merge <branch>

Graphical tool to go through merge conflicts

	git mergetool


### Log

	git log
	git log --author=marek
	git log --pretty=oneline
	git log --graph --oneline --decorate --all

See only files changed

	git log --name-status

Complete diffs at each step

	git log -p

Overview of the change

	git log --stat --summary
	git log --since=2.weeks

### Config

	git config --list
	git config --global user.name "mpoks"
	git config --global user.email "marek.poks@axit.pl"
	git config --global core.editor mcedit
	git config --global credential.helper store

Keep credentials in memory

	git config --global alias.co checkout

Aliases

	git config --global alias.br branch
	git config --global alias.ci commit
	git config --global alias.st status
	git config --global alias.unstage 'reset HEAD --'
	git config --global alias.last 'log -1 HEAD'

	git help <command>
	full help
	git <command> -h
	short help

-------------------------------------------------------------
	undo git clone --single-branch
	git config remote.origin.fetch "+refs/heads/*:refs/remotes/origin/*"
	git fetch origin
