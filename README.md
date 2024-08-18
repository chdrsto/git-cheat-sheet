# Cheat Sheet and Documentation on how to use Git and Github
This respository will only have a README file and describe the tasks and activities on how to use Git and Github.
It is mainly based on the git-cheat-sheet PDF from the GitHub Education page [LINK](https://education.github.com/git-cheat-sheet-education.pdf)
I'm not a developer and do not contribute a lot of code. Hence, I dont often work with git and have to use a cheat sheet to remember how things work. If it is useful for others, fine but it will never be a full comprehensive documentation for git and github.
Its a survival sumary for git basically.

## Setup user parameter and variables used by git
Configuring user information used across all local repositories
```bash
git config --global user.name "[firstname lastname]"
git config --global user.email "[valid-email]"
git config --global color.ui auto
```
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
