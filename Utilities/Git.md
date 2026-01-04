tag: #git-list
## List commits
```bash
git --no-pager log --pretty=format:"%h - %an, %ar : %s" -10
```
(use *q* to exit the list)
(See this [web page](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History))
## Rewind a project to a specific commit
tag: #git-rewind
```bash
git reset --hard c1ed06c
```
## Link an existing project with a repository on bitbucket
Use my script:
```bash
gitinit <your_remote_repository_url>
```
Which performs:
```bash
git init
git config credential.helper store
git add .
git commit -m 'Initialise'
git remote add origin <your_remote_repository_url>
git push -u origin master
```
## Initialise a git directory
```bash
git init
```
## Align local with remote repository
```bash
git checkout master &&
git fetch origin &&
git reset --hard origin/master
```
## Save username and password
```bash
git config credential.helper store
```
## Remove a file from a repository
```bash
git rm --cached app.log
```
```bash
git commit -m "remove app.log"
```
## Basic git push workflow
```bash
git add .
git commit -m "<description>"
git push origin master
```
creates a *.git* directory (a *repository*) in the *working directory* and makes git functionality available.
## clone
```bash
git clone <url of website>
```
creates a directory with the same name as the repo and downloads from the *remote origin* all of the files in the repo.
## Git Status
```bash
git status
```
displays information about files that have been modified.
Before any modifications:
>On branch master
>
>Your branch is up-to-date with 'origin/master'.
>
>nothing to commit, working tree clean
## branch
```bash
git branch branch_01
```
This creates a *reference* or *checkpoint*. (*commit*s are a special sort of *reverence* of *checkpoint* called a *revision*.)