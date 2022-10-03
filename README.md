# MOST USEFUL KNOWLEDGE NUGGETS ABOUT GIT & GITHUB

## TOP BEST GIT TOOLS & LEARNING RESOURCES
[git cheatsheet dot org](https://gitcheatsheet.org/how-to) - a tonne of most useful easy as a piece of cake explained "how to" do x code snippets  
[git essentials](https://www.udemy.com/course/git-and-github-tutorial) - best git & github tutorial in english by kalob taulien of [kalob.io](https://kalob.io) and [gitforeverybody.com](https://gitforeverybody.com)  
[git book](https://books.goalkicker.com/GitBook) - superbly comprehensive, in depth and advanced git bible  
[advanced git kit](https://www.git-tower.com/learn/git/advanced-git-kit) - a set of advanced git helpers (tools) by the creator of [git tower](https://www.git-tower.com)  
[learn git branching](https://learngitbranching.js.org) - online visualisation tool for learning branching in git  
[gitignore.io](https://gitignore.io) - tool for generating gitignore files  
[dillinger.io](https://dillinger.io) - WYSIWYG editing tool for markdown files  
[markdown explanation](https://daringfireball.net/projects/markdown) - a robust explanation of markdown by john gruber  
[markdown cheatsheet](https://www.markdownguide.org/cheat-sheet) - a cheatsheet by [markdown guide](https://www.markdownguide.org) listing markdown edit options

## WINDOWS & MAC TERMINAL COMMANDS USEFUL FOR GIT BASH
ls - lists directory files  
ls -la - lists directory files  
ls -al - lists directory incl. hidden files  
clear - clears terminal  
pwd - lists current directory path (tells you where you are with terminal)  
cd - change directory to home  
cd dir - change directory to directory  
mkdir dir - create directory named directory  
rm file - remove file  
rm -r dir - remove directory  
touch - creates a new file in mac  
echo - creates a new file in windows

## GENERAL GIT SIDE NOTES & MENTAL NOTES TO SELF
- **github** is a **vcs** - version control system
- **staging** = **indexing**
- **pull request** = **merge request**
- **merge** and **rebase** both integrate into **head branch**
- **merge** is **fast forward** per default
- **branches** created in local repo must be **pushed to remote origin** to be listed & operable there
- git **commit title** can have up to 72 characters but best fit within 50 (if you don't fit you're doing too large commits -> make more frequent smaller commits)
- git **push** uploads new, modified and deleted files and branches to remote origin, but git **pull** downloads new, modified and deleted files and only downloads new - - and modified branches - it does not download & sync deleted branches. to delete a branch git pull is not enough, it won't apply this change. you need **pruning** for this. [more details on this](https://railsware.com/blog/git-housekeeping-tutorial-clean-up-outdated-branches-in-local-and-remote-repositories) 
- you can't **delete** the **head branch** (the branch you're "sitting on" - currently active / pointed to branch)
- best not **rename commits** already on **remote origin** (especially when workign with a team)
- best not use **rebase** on **remote origin** (especially when workign with a team). if you must just don't rebase on main so that main branch commits won't change.
- git **rebase squashing** - choose which commit to squash, will merge this commit with the one above it
- git **reflog** is the history of **local repository** (local history)
- git **stash** can have **branches**
**asterisk * ** is not a part of git, it's a bash wildcard, best not use it as it can lead to unexpected results

# MOST USEFUL GIT COMMANDS

- **IMPORTANT** - below commands use a format of () - inside brackets = description of what should go there, () is just a placeholder indicating beginning & end of that thing that should be placed there - **remove the brackets from the real command you type into terminal**

## CONFIGURE GIT ON YOUR LOCAL MACHINE

/ check current text editor

    git config --global core.editor

/ set global text editor to VS code

    git config --global core.editor "code --wait"

/ set global text editor to notepad++ with blank new window, no tabs

    git config --global core.editor "'C:/Program Files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"

/ set global text editor to subline text

    git config --global core.editor "'C:/Program Files (x86)/sublime text 3/subl.exe' -w"

/ set up github user & email

    git config --global user.name "(your user name)"
    git config --global user.email "(your email)"

## START A GIT PROJECT

/ download git project to your local device - optionally put the name of the folder into which it will be downloaded, otherwise this folder will be named same as it is named on github (will use the remote repository name)

    git clone (path.git here) (*optional: name of your local folder here)

/ turn a folder on your computer into a git repository (initialize a repository)

    git init

/ add a remote repository

    git remote add origin (path.git here)

/ set the origin branch of a repository

    git remote set-url origin (path.git here)

## GIT BRANCHES

/ return info on current branch

    git branch

/ create a new branch

    git branch (new branch name)

/ create a new branch and switch to it

    git checkout -B (new branch name)
    OR
    git switch -c (new branch name)

/ switch to a different branch

    git checkout (name of the branch you want to switch to)
    OR
    git switch (name of the branch you want to switch to)

/ switch to the previous branch

    git checkout -

/ rename the local branch you are on

    git branch -m (new name for the branch you're on)

/ rename a local branch you are not on

    git branch -m (old branch name) (new branch name)

/ rename a remote branch (effectively delete it and push it uploading it again)

    git push origin --delete (name of the branch you want to rename)
    git push -u origin (new name for the branch)

/ see the state of your local branch versus the remote counterpart

    git branch -v

/ list all the branches

    git branch -a

/ compare two branches

    git log (branch1 name)..(branch2 name)
    
/ merging data from x branch to current local head branch

    git checkout main
    AND
    git merge (name of the branch you want to integrate data from to main)
    OR
    git merge --no-ff (name of the branch you want to integrate data from to main)
    OR
    git merge --no-ff (branch name) -m "(your commit description)
    OR
    git rebase (name of the branch you want to integrate data from to main)

[more details on merging differences here](https://stackoverflow.com/questions/6701292/git-fast-forward-vs-no-fast-forward-merge)

/ delete a local branch

    git -d (branch name)

/ delete a local branch very much

    git -D (branch name)

/ delete a remote branch

    git push origin --delete (branch name)

## GIT STAGING (INDEXING) & COMMITTING

/ stage / index a file - add a file from working area to staged area

    git add (file_name.extension)

/ stage / index files - add files from working area to staged area

    git add -A              // all directories & subdirectories, untracked, new, tracked, modified, deleted
    git add --all           // all directories & subdirectories, untracked, new, tracked, modified, deleted
    git add .               // current directory, subdirectories, untracked, new, tracked, modified, deleted
    git add -u              // current directory, subdirectories, tracked, modified, deleted
    git add --update        // current directory, subdirectories, tracked, modified, deleted
    git add *.(file type)   // adds only files of a certain type (by extension)

/ remove a file

    git rm -r (file_name.extension)

/ unstage - remove a file from staging area back to workspce (unstage a file)

    git restore --staged (file_name.extension)
    git reset HEAD (file_name.extension)

/ undelete - restore a deleted file

    git checkout -- (file_name.extension)

/ discard changes done to a file (restore a file)

    git checkout -- (file_name.extension)

/ view file details

    git cat (file_name.extension)

/ compare the committed file and modified file versions

    git diff (file_name.extension)

/ commit staged files to local repository

    git commit -m "(your commit description title)"

/ commit staged & unstaged files to local repository

    git commit -u -m "(your commit description title)"

/ commit all (incl. unstaged and ignored) files to local repository

    git commit -a -m "(your commit description title)"

/ commit with description title & body

    git commit -m "(your commit description title)" -m "(your commit description body)"

/ change the title of the last committed commit

    git commit --amend -m "(your new & amended commit title)"

/ rename several past committed commits (edit commit messages)

    git rebase -i HEAD~(number indicating how deep into past commits you want to go to edit)  
    
/ add files to the last committed commit

    (change / add some file)
    git add . 
    OR
    git add (changed / added file.extension)
    AND
    git commit --amend

/ show details of a committed commit

    git show (commit id)

## GIT PUSH TO REMOTE ORIGIN & PULL TO LOCAL REPO

/ push changes committed to local repo to main/master* branch of git remote origin - * watch out for your main branch name not to make a new branch with a different name

    git push
    OR
    git push origin main/master

/ push changes committed to local repo to a different branch of git remote origin when that different branch was only created locally and doesn't exist on remote origin yet (needs to be created)

    git push -u origin (different branch name)
    OR
    git push --set-upstream origin (different branch name)

/ push changes committed to local repo to a different branch of git remote origin

    git push origin (different branch name)

/ set up a tracking connection between a remote origin branch and local repo (sets up a local branch copy)

    git branch --track (branch name) (location of the branch on origin)
    OR
    git checkout --track (location of the branch on origin)

/ pull changes from remote origin * and/or branch (if no branch indicated, will pull from main) to local repo

    git pull (*optional: branch name)
    
/ fetch + merge (= pull) changes from remote origin * and/or branch (if no branch indicated, will pull from main) to local repo

    git fetch (*optional: branch name)
    git merge (*optional: branch name)

## GIT STATUS CHECKING & HISTORY AUDIT

/ show git remote origin source

    git remote -v
    
/ return info on current branch, status of files (unstaged, staged etc.)

    git status

/ return info on the current branch & status of uncommitted files (unstaged, staged etc.) + displays all untracked files & folders (including those ignored by .gitignore)

    git status -uall
    
/ list all previously done commits

    git log

/ list x number of last commits

    git log -(x number)

/ list all previously done commits of x user

    git log --author=(x user)

/ list all commits done by x date (date format YYYY-MM-DD)

    git log --before "(x date)"

/ list all commits done after x date (date format YYYY-MM-DD)

    git log --after "(x date)"

/ list all commits done after x date & before y date (date format YYYY-MM-DD)

    git log --after "(x date)" --before "(y date)"

/ list all previously done commits 1 line per commit

    git log --oneline

/ list all previously done commits 1 line per commit in a fancier way

    git log --oneline --graph --all

/ list all previously done commits and show changes they implemented

    git log -p

/ list all previously done commits and show their general stats

    git log --stat

/ list all previously done commits with a certain keyword

    git log --grep="(certain keyword)"

/ list all previously done commits regarding a certain file (if file is in a folder, path must be included)

    git log -- (certain file)

/ list all previously done commits by hash id, author id and commit date

    git log --pretty="(Hash: %H, Author: %aN, Date: %aD)"

/ list all previously done commits in most fancy way in git gui

    gitk --all

/ list all previously done commits by title grouped by user

    git shortlog
    
## AMENDING GIT HISTORY & FIXING REPO MISTAKES

/ restore the state from x previous commit - creates a new commit using a past committed indicated commit

    git revert (x commit id)

/ restore the state from x previous commit - undoes newer commits + unstages their changes

    git reset (x commit id)

/ restore the state from x previous commit - undoes newer commits + their changes moved to staging area

    git reset --soft (x commit id)

/ restore the state from x previous commit - undoes newer commits + removes these commits + removes their changes & files

    git reset --hard (x commit id)

/ merge commits together into 1 parent commit 

    git rebase -i (parent commit id)

/ merge commits together into 1 parent commit 

    git rebase -i HEAD~(number of commits to merge)

/ merge & squash merges & squashes but leaves files staged, need to be committed

    git checkout
    git merge --squash (name of the branch you want to integrate data from to main)

/ clone x commit to main (creates a new copy of x commit on main & merges it with main)

    git checkout main
    git cherry pick (x commit id)

/ clone x commit to main (creates a new copy of x commit on main & stages it on main)

    git checkout main
    git cherry pick (x commit id)

## GIT STASHING

/ stash changes

    git stash
    OR
    git stash save "(your stash commit description)"

/ show stash changes

    git stash list

/ show stash changes with details

    git stash show (stash commit id) -p

/ retrieve the changes from stash back to work area

    git stash apply

/ retrieve the changes from stash back to work area + delete stassh commit from stash list

    git stash pop
    OR
    git stash pop (stash commit id)

/ delete stash commit

    git stash drop (stash commit id)

/ delete stash commits - all

    git stash clear

## SPECIAL PRETTY REPORT LOG CODE FROM KALOB TAULIEN

    git log --topo-order --all --graph --date=local --pretty=format:'%C(green)%h%C(reset) %><(55,trunc)%s%C(red)%d%C(reset) %C(blue)[%an]%C(reset) %C(yellow)%ad%C(reset)%n'



