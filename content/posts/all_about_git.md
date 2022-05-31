---
title: "Learning Git"
date: 2022-05-31
author: "Me"
draft: false
---

**SCM** : Source Control Management.

**VCS**: Version Control System.

> All of the content here is for command line, as I am very comfortable with terminal [*and of course Linux*].



Basic git syntax: `program | action | destination`.

*For example*: `git | add | .`



# Configure git

```bash
# set your name
$ git config user.name "user-name"

# set your email
$ git config user.email "user-email@example.com"


# set global user name
$ git config --global user.name "username"

# set global user email
$ git config --global user.email "user-email"
```

# Basic

```bash
# to check git version
$ git --version

# initializing git repository
$ git init

# check status of the git repo
$ git status

# clone remote repo to your machine
$ git clone [url]

# Add all files at once
$ git add .

# Add specific files by name
$ git add {file-name/path-to-file}

# commit all the files
$ git commit -m "messages you want to write"

# to correct/amend commit message
$ git commit --amend -m "your message"

# commit with title & description
$ git commit -m "Title" -m "Description..."

# to view specific commit
$ git show {commit-ID}

# to update every change
$ git add -u

# to remove file
$ git rm {file-name}

# remove file from git staging area
$ git rm --cached {file-name}

# to untrack all files in git-ignore
$ git rm -r --cached .

# restore staged file
$ git restored -staged {file-name}

# configure git to ignore specific file
$ echo {file-name} >> .gitignore

# to move or rename file
$ git mv {old-file-name} {new-file-name}

#  to restore file from last commit
$ git checkout -- {file-name}

# to restore all file from last commit
$ git checkout -- .

# to restore file from a commit and move to current branch
$ git checkout {commit-ID} -- {file-name}

# check help menu
$ git help log 
```

# Update & Delete

```bash
# to test delete untracked file
$ git clean -n

# to delete untracked file
$ git clean -f

# to unstage / undo adds
$ git reset HEAD {file-name}
```

# Git Log

```bash
# list of git log
$ git log

# view logs in oneline (awesome!)
$ git log --oneline

# list of changed files
$ git log --name-only

# to view commit log in one line with full SHA-1 format
$ git log --format=oneline

# to view changes
$ git log -p

# to view commits of a specific file
$ git log {file-name}

# to view all commits of a specific file
$ git log -p {file-name}

# to view status & summary of commits
$ git log --stat
$ git log --stat --summary

# to view commit history in graph
$ git log --graph

# to view summary of commit history in graph
$ git log --oneline --graph --all --decorate

# view previous commit history
$ git log --graph --decorate
```

# Git Branch

```bash
# create a new branch
$ git branch {branch-name}

# switch to an existing branch
$ git checkout {branch-name}
$ git switch {branch-name}    # new

# create a new branch and swithc to it
$ git checkout -b {branch-name}

# rename branch
$ git branch -m {branch-name} {new-branch-name}
$ git branch --move {old-branch-name} {new-branch-name}

# to show all branches that are merged into current branch
$ git branch --merged

# delete a branch
$ git branch -d {branch-name}

# list all branches
$ git branch

# view all branches - local & remote
$ git branch -a

# to remove remote branch
$ git push --delete origin {branch-name}

# to delete unmerged branch
$ git branch -D {branch-name-to-delete}
```

> **HEAD** is where we right now in the repository. The **HEAD** points to the last commit in the branch we  are currently on.

# Git Merge

There are two types of merging:

1. **Fast-forward-merge**: It happens when current branch has no extra commits compared to the branch we're merging.

2. **No-fast-forward-merge**: If the master branch has new changes which other branch doesn't have, git will commit no-fast-forward merge.

```bash
# first checkout to master branch
$ git checkout master

# merging
$ git merge {branch-name}

# to merge on master branch (only if fast forward)
$ git merge --ff-only {branch-name}

# merging on master branch (forcing a new commit)
$ git merge --no-ff {branch-name}

# to stop merge (in case of conflicts)
$ git merge --abort
$ git reset --merge		# prior to v1.7.4

# to undo local merge
$ git reset  --hard {branch-name}

# to merge a specific commit
$ git cherry-pick {commit-ID}

# rebase
$ git checkout {branch-name} >> git rebase main

# to cancel rebase
$ git rebase --abort

# Squash multiple commit to one commit
$ git rebase -i HEAD~3

# to squash merge in one commit
$ git merge --squash {branch-name}  # (and commit afterwards)
```

# # Git Stash

```bash
# save into stash
$ git stash save "message"

# show list of the stash
$ git stash list

# show stash status
$ git stash show {stash-ID}

# show changes on stash
$ git stash show -p {stash-ID}

# to bring all stash
$ git stash pop

# to bring specific stash
$ git stash pop {stash-ID}

# to use specific stash without dropping
$ git stash apply {stash-ID}

# use custom stash and index
$ git stash apply --index

# create new branch from stash
$ git stash branch {new-branch}

# to delete 1st item of stash list
$ git stash drop

# to delete specific stash from stash list
$ git stash drop {stash-ID}

# to delete the whole stash
$ git stash clear
```

# Git Compare

```bash
# show difference
$ git diff {commit-ID} {commit-ID}

# compare modified files and highlight changes
$ git diff --color-words {file-name}

# view the difference between last commit and staged version
$ git diff --staged

# to compare branches
$ git diff main..{branch-name}
```

# Working with remote repository

```bash
# initilizing remote repository
$ git remote add origin {connection-string.git}

# list remote repository
$ git remote -v

# pushing repository
$ git push origin master/main

# clone repo
$ git clone <ssh-link>

# update the repo
$ git fetch origin master

# fetch & merge remote changes
$ git pull origin master
```

# Using SSH

```bash
$ git remote -v
$ git remote set-url origin git@github.com:username/repo-name.git
```

No need to give password every time.

# Git Settings with GitHub

Silly, but this section is for myself. :P

```bash
$ ssh-keygen -t rsa -b 4096 -C "githubMail"
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa
$ vim .ssh/id_rsa.pub    # copy the value inside
$ ssh -T git@github.com
```
