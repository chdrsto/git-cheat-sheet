# Cheat Sheet and Documentation on how to use Git and Github
This respository will only have a README file and describe the tasks and activities on how to use Git and Github.
It is mainly based on the git-cheat-sheet PDF from the GitHub Education page [LINK](https://education.github.com/git-cheat-sheet-education.pdf)
I'm not a developer and do not contribute a lot of code. Hence, I dont often work with git and have to use a cheat sheet to remember how things work. If it is useful for others, fine but it will never be a full comprehensive documentation for git and github.
Its a survival sumary for git basically.
## SETUP
### Setup user parameter and variables used by git
Configuring user information used across all local repositories
```bash
git config --global user.name "[firstname lastname]"
git config --global user.email "[valid-email]"
git config --global color.ui auto
```
### Setup and initialize the first project on the shell
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
### Clone from Repository
This retrieves an entier repository from ta hosted location via SSH
```bash
git clone git@github.com:chdrsto/projeqtor.git
```
## STAGE & SNAPSHOT
Working with snapshots and the Git stating area
```bash
git status

git add [file]     # Add a file as it is now to the next commit (stage)
git add .     # Add all files within this and sub-directories to the next commit (stage)

git reset [file]     # unstage (remove) a file from the reqpository retaining the changes in working directory

git diff     # Shows differences on what is changed but not staged
git diff --staged     # diff of what is staged but not yet committed

git commit -m "[descriptive message]"     # Commit your staged content as a new commit snapshot
```

## BRANCH & MERGE
A branch is needed if you temporarly want to clone the main branch to perfrom some activities without affecting the main branch until the task is done. This is used to develop new features or bugfixing without impacting the main branch until it is complete and tested.
Once the activities are done, it needs to be merged back to the main branch and can be deleted.
```bash
git branch     # List all existing branches. The currently active branch will be marked with a star (*)
git branch [branch-name]     # Create a new branch
git switch [branch-name]     # Set another branch active and mark it with a star (*)
git checkout     # Switch to another branch and check it out into your working directory

git merge [branch]     # Will merge the active branch with the provided branch
```
## INSPECT & COMPARE
Examing logs, diffs and object information
```bash
git log     # Will show all commits in the current active branch
git log branchB..branchA     # Show all commits on branchA which are not on branchB
git log --follow [file]     # Show the commits that changed file, even across renames

git diff branchB...branchA     # Show the diff of what is in branchA that is not in branchB

git show [SHA]     # Show any object in Git in human-readable format
```

## TRACKING CHANGES
Versioning file removes and path changes
```bash
git rm [file]     # Delete the file from project and stage the romal for commit
git mv [existing name] [new name]     # Change an existing file name
git log --stat -M     # Show all commit logs with indication of any paths that moved
```

## SHARE & UPDATE
Retrieving updates from another repository and updating local repos
```bash
git remote add [alias] [url]     #add a git URL as an alias
git fetch [alias]     #fetch down all the branches from that Git remote
git merge [alias]/[branch]     # Merge a remote branch into your current branch to bring it up to date
git push [alias] [branch]     # Transmit local branch commits to the remote repository branch

git pull     # Fetch and merge any commits from the tracking remote branch
```

## Passwordless authentication on Github
Pushing code to github requires authentication. Using SSH keys allow a strong but passwordless authentication method. This steps describe on how to use this.
Login to the terminal on the system where yo udevelop and push code to github
```bash
ssh-keygen -t ed25519 -C "email@domain.com"    # Generate the key and sed a strong passphrase

eval `ssh-agent -s`     # Use the generated key
ssh-add ~/.ssh/id_ed25519.pub

cat ~/.ssh/id_ed25519.pub     # Print the public key file and copy it to the clipboard
```
Open GitHub SSH creator page in the Browser [LINK](https://github.com/settings/ssh/new)
Create a new SSH Key
Paste the public key from the clipboard into the Key-Field on GitHub and save

Check if the connection works
```bash
ssh -T git@github.com
```
Connect to the remote repository using SSH
```bash
git remote -v     # In case of https:// ... it needs to be changed to use SSH instead (continue)

# Switch remote URLs from HTTPS to SSH type:
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git

```
