# Cheat Sheet and Documentation on how to use Git and Github
This respository will only have a README file and describe the tasks and activities on how to use Git and Github.


## Setup user parameter and variables used by git
Configuring user information used across all local repositories
```bash
git config --global user.name "[firstname lastname]"
git config --global user.email "[valid-email]"
git config --global color.ui auto
```
For adding

## Setup and initialize the first project on the shell
```bash
cd /path/to/the/project
git init
git status
git add .
git commit -m 'create a first commit'
git branch -M main
```
Create a new repository and push the code to Github
```bash
git remote add origin https://github.com/chdrsto/xxx.git
git push -u origin main
```

## STAGE & SNAPSHOT

## BRANCH & MERGE

## INSPECT & COMPARE

## TRACKING CHANGES

## SHARE & UPDATE
