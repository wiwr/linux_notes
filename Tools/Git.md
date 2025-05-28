## Check git configuration
```bash
git config --global --list
```
## Configuring Git
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global core.editor "your text editor"
```
When used without parameter can be use to check current value

```bash
git config --global init.defaultBranch main
```
Configuration to make that match to GitHub
## Git version
```bash
git verison
```
### Keys for github
```bash
ssh-keygen -t rsa -b 4096
cat ~/.ssh/id_keyForGitHub
```
on GitHub go to settings and SSH and GPG keys

```bash
ssh -T git@github.com
eval `ssh-agent -s`
ssh-add ~/.ssh/id_keyForGitHub
```
Config file for SSH to point git
```bash
Host github.com
	HostName github.com
	User git
	IdentityFile ~/.ssh/git_key
```
## Initialize Git
```bash
git init
git init -b main
```

## Check status
```bash
git status
```

## Git add
```bash
git add -A
git add .
git add index.html
git add index.html style.css
```

## Git commit
```bash
git commit -m 'Initial commit'
git commit -am 'Added new thing'
```

## Git log
```bash
git log
git log --all
```

## Git remote
```bash
git remote add origin <git_repo>
git remote
git remote -v
```

## Git Branch
```bash
git branch -M main
git branch
git branch --all
git branch <name_of_new_branch>
git branch -vv
git branch -u <shortname>/<branch_name>
```
to remove branch

```bash
git branch -d feature/new_function
```

## Git Checkout
```bash
git checkout -b feature/new_function
git checkout <branch_name>
git checkout <commit_hash>
```
## Git switch
```bash
git switch <branch_name>
git switch -c <new_branch_name>
```
## Git Push
```bash
git push origin main
git push -u origin main
git push
git push -u origin feature/new_function
```
## to remove branch
```bash
git branch --all
git push origin -d feature
git switch main
git branch -d feature
git branch --all
```
## to remove branch when remote is removed
```bash
git branch --all
git fetch -p
git branch --all
git branch -d feature
git branch --all
```
## Git Pull
```bash
git pull
git pull origin main
```
Get the latest changes from a repo
## Git .gitignore
File to list resources that should be included in repo

## two commends
```bash
git add . && git commit -m "added new changes"
```
## more in one
```bash
alias.ac=!f() { git add . && git commit -m "$1"; }; f 
alias.acp=!f() { git add . && git commit -m "$1" && git push; }; f
```
### better version
```bash
alias.ac=!f() { git add -A && git commit -m "$1"; }; f 
alias.acp=!f() { git add -A && git commit -m "$1" && git push; }; f
```
## Git clone
Get a copy of the full repo on to your machine
```bash 
git clone <git_repo>
git clone <git_repo> .
git clone <git_repo> <folder_name>
```
## Git fetch
Get latest changes without merging
```bash
git fetch -p
```
## Forking
Copy a repository into your own account

## git merge
```bash
git merge feature/new_function
git merge origin/mian
git merge --abort
```

### git merge remote to local
```bash
git fetch
git merge origin/main
```

## Git cat-file
```bash
git cat-file -p <commit_hash full| comit_hash 7 char>
```


```bash
echo "# linux_notes" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:wiwr/linux_notes.git
git push -u origin main
```

```bash
git remote add origin git@github.com:wiwr/linux_notes.git
git branch -M main
git push -u origin main
```

# Debug
### Asking for password
Check remote URL
```bash
git remote -v
```
Check ssh config file

Change to ssh
```bash
git remote set-url origin git@github.com:wiwr/linux_notes.git
```

