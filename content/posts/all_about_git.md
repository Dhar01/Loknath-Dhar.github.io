---
title: "Learning Git"
date: 2022-05-31
author: "Me"
draft: false
---

**SCM** : Source Control Management.

**VCS**: Version Control System.



> All of the content here is for command line, as I am very comfortable with terminal [*and of course Linux*].

### Configure git

```bash
# set your name
$ git config user.name "user-name"

# set your email
$ git config user.email "user-email@example.com"
```



### Basic

```bash
# to check git version
$ git --version

# initializing git repository
$ git init

# check status of the git repo
$ git status

# Add all files at once
$ git add .

# Add specific files by name
$ git add <file-name>

# commit all the files
$ git commit -m "messages you want to write"

# remove file from git staging area
$ git rm --cached <file-name>

# restore staged file
$ git restored -staged <file-name>

# configure git to ignore specific file
$ echo [file-name] >> .gitignore

# check help menu
$ git help log
```

### Git Logs

```bash
# list of git log
$ git log

# view logs in oneline (awesome!)
$ git log --oneline

# list of changed files
$ git log --name-only

# view previous commit history
$ git log --graph --decorate
```

### Git Branches

```bash
# create a new branch
$ git branch <branch-name>

# switch to an existing branch
$ git checkout <branch-name>

# create a new branch and swithc to it
$ git checkout -b <branch-name>

# delete a branch
$ git branch -d <branch-name>

# list all branches
$ git branch

# view all branches - local & remote
$ git branch -a
```

> **HEAD** is where we right now in the repository. The **HEAD** points to the last commit in the branch we  are currently on.

### Merging

```bash
# first checkout to master branch
$ git checkout master

# merging
$ git merge <branch-name>
```

There are two types of merging:

1. **Fast-forward-merge**: It happens when current branch has no extra commits compared to the branch we're merging.

2. **No-fast-forward-merge**: If the master branch has new changes which other branch doesn't have, git will commit no-fast-forward merge.



### Working with remote repository

```bash
# initilizing remote repository
$ git remote add origin <connection-string.git>

# list remote repository
$ git remote -v

# pushing repository
$ git push origin master

# clone repo
$ git clone <ssh-link>

# update the repo
$ git fetch origin master

# fetch & merge remote changes
$ git pull origin master
```
