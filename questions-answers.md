# Git Questions & Answers

(Questions from [Knowledge Hut's "Git Interview Questions"](https://www.knowledgehut.com/interview-questions/git), answers by me )

![My Favourite Git Data Transport Commands Diagram](https://www.stephenmarron.com/wp-content/uploads/2017/02/git.png)

### Q: What is a git commit?
****A:**** A commit is a group of changes ssaved to the Git repository.

### Q: What is a git branch?
**A:** A branch can be described as a timeline (history of adding) of commits. When starting with a Git repository we begin with only 1 branch called "main", it is the primary banch. Other branches can be added if working on the files from main without immediately affecting them is necessary. Other branches can then be merged with the main branch once work there is completed and can be joined without problems. The other branch can be deleted after it's fulfilled its use (its contents were merged with main branch's contents) or can be kept for legacy/work history purposes.

### Q: How to check if git is installed?
**A:** To check if git is installed one can run the command "git version" in the command terminal - the response can be either the version fo the git which is installed, or an information that git is not installed (no version available). 

### Q: How to get help with various git commands?
**A:** To get more detailed information on a particular git command the command "git help (command_name)" can be run in the command terminal.

### Q: How to check the current status of the local repository?
**A:** To check the current status of the local repository one could run the ever so popular & useful command "git status" in the command terminal. The answer returned in the terminal will include the current location of HEAD (name of the branch HEAD is currently on) and the list of all wiles in the working area & staging area (new and untracked & modified and tracked files - meaning it will not tell us about deleted or committed files, as well as about the ignored files) - if there are no such files, the answer will also include the statement that there are no new/modified files ("working directory clean").

### Q: What are the steps to a unstage file?
**A:** To remove a file from the staging area (unstage it) we can run the "git reset (filename.extension)" command in command terminal. Unstaging a file will move it from staging area to the working area.

### Q: How to discard modifications done in a file?
**A:** To discard any modifications we have done in some file, we need to move it back to the working area of a branch first, and then remaining on this branch, we can call the last "saved" (so "committed") version of this file in our local git repository using "git checkout (filename.extension)". We don't really tell git to "discard new changes", we just replace the new version of the file (the one with changes) with the last saved "unmodified" version without these changes.

### Q: What is git stash?
**A:** Git stash is a temporary cache for our data - when working with git on a branch, if we need to drop everything and go work somewhere else, we can save our unfinished work to a stash - this clears our working area of the files we were working on (working area empty) without the need to commit the files (because they are not ready to be "saved" and committed), and we can then workon something else. Once that's done and we're ready to resume the work we've stashed, we can call those files back, they will be returned to us just in the state they were in when we've stashed them.

### Q: What is the difference between git pull and git fetch?
**A:** Git pull performs git fetch (so downloading the data from remote origin repository to our local repository) and git merge (so applying these changes onto our local repository) as one action, without the possibility to review the fetched updates. Git fetch only downloads the updates from the remote origin, does not immediately merge (apply) them, allowing us to view the updates and choose which we want to apply.

### Q: How to revert the previous commit in git?
**A:** Since --amend only works for the immediate last commit, to reach older commits we need to use the command git reset (id of the commit to which we want to revert to). This will return the state of the commit of which id we've input into the command - without any modificators, this will unstage the newer commits, with modificator --soft this command will return these commits' changes into the working area, and with the --hard modificator it will remove these commits, their files and all their changes entirely.

### Q: What is the difference between HEAD, working tree and index in git?
**A:** They are together called the "Three Trees of Git". HEAD is a pointer which points to only 1 branch and 1 commit at the time, per default it is always the top newest commig of the current branch - you can switch between branches (horizontally) and commits (history of the branch, vertically) using git checkout for example.

The working tree is the folder and subfolder structure of the directory initialised as the git repository. The index is the staging area, it's the area where ready to be committed (saved) files are awaiting to be commited (saved). In "reality" it is a file inside of the git folder of our git repository where the information about files added to the staging area is stored.

### Q: How to remove a file from git without removing it from your file system?
**A:** Sometimes we may end up adding files in our commit which we never intended to commit. Nothing to worry if you come across a scenario. The command git rm will remove it from both your staging area (index), as well as your file system (working tree), which may not be what you want.
We can use git rm --cached on the file if you want to remove from the version control cache but do not want to remove/delete from your filesystem. So if you wanted to remove foo.txt from version control like this just run git rm --cached foo.txt
We can also use git reset (filename.extension) to achieve the same result - it undoes the local changes.

### Q: Explain the advantages of Forking Workflow.
**A:** The Forking Workflow means that each developer receives a fork (a copy linked to the original repository) of the chief/main repository of their own, and if they want to push shome finished changes/updates to the original repository, they need to do this via making a pull request - meaning the original repository's owner would need to review the proposed changes and decide if to apply them or not (review the pull request before merging it with their repository, the original repository, source for all forked repositories). This workflow is used with most open sourcee projects - if someone thinks they can improve it, they fork the original repository, work on their improvement, and once it is ready to deploy as a new feature of the original project, ask the owner of the original project to implement their update in the original project.

### Q: What is cherry picking in git?
**A:** Cherry picking in git is when we take one singular commit from some branch and merge it with another branch. It does not move this commit (cut out and paste into another branch), it creates a new copy of that commit on our target branch with a new commit id. It is useful when we don't want to merge the whole branch into another branch, but need a specific part of that branche's history, just one commit - the newer and older commits, all of the rest of that branch's commit history will remain as it is.

### Q: What is git fork? What's the difference between fork, branch and clone?
**A:** A fork is a copy of the whole repository - we have an origin repository on Git, and we want to work on it, so we makake a fork of it - our own copy. This is different from cloning because forked repositories are linked to the original ones (the original repository has a list of forks, and the forked repo has a link in the description showing where is the original source of that project) and cloning a repository does not leave any links to the original repository. Because forks are linked, if we make an update, we can ask the owner of the original repository to implement it in the original project source as an update via a pull request. Cloning is not linked to the original source, it's its own standalone copy, so this option of updating the original source is unavailable with cloning. Each time a project is forked, the owner of the original source is notified, but downloading the project as a zip file or cloning does not leave such traces.
Branches are different from these, they are commit timelines within 1 repository. A repository can have 1 branch or many branches. They are usually created to develop some side feature without disturbing the last working version of the project, and once that feature is developed, the branch can be merged with the main branch and deleted (or not, or it can be left for history transparency).

### Q: What language is used in Git?
**A:** Git as a tool is written using mostly C (45%) and Shell (35%) with bits of Perl, TCL, Python and C++. Its most prominent features are:
- Strong support for non-linear development.
- Compatibility with existing systems and protocols
- Efficient handling of large projects
- Cryptographic authentication of history
- Toolkit-based design.

### Q: What does git push do in git?
**A:** Git push uploads the local commits to the remote origin repository - it will source the commits from teh current local repository, so the branch with the HEAD pointer on the local repository, and the branch where these commits are deposited (uploaded to) on remote origin repository can be additionally indicated in the git push command - if not indicated, the changes (new commits) will be uploaded to the main branch. The construction of the command is as follows - git, we call the git command ; push, we tell git to upload the commits from our local repository ; origin, we tell git to upload the commits to the remote origin repository, and ; the n as 4th we can specify the branch by adding the branch name.

### Q: What's the difference between Git and SVN?
**A:** Git is decentralised while SVN is centralised.
Git vs. SVN :
1. Decentralized vs. Centralized
2. 3rd gen vs 2nd gen
3. We can clone the entire repo on our local systems vs. Version history is stored on a server-side repository
4. The commits are possible even if remote repo not available vs. Committing available when connected to the main repo (server-side)
5. The basic push/pull operations are faster vs. The basic push/pull operations are slower
6. Work is shared automatically by commit vs. Nothing is shared automatically, you need manual intervention

### Q: What is the HEAD in git?
**A:** HEAD is a kind of a pointer in git which informs us of our current location. When switching branches, HEAD points to the newest commit of the branch (the topmost, latest commit in that branch - remember, a branch can be imagined as a timeline of committed commits, a history/tree of commits). HEAD can however point to any of the commits in the branch, as we can view them, so if we call onto some older commit, HEAD (our current location) will change to that commit.

### Q: What are the most common version control systems?
**A:** 
#### 1: GitHub
It's as yet the biggest network site for programming advancement, despite everything it has probably the best apparatuses for issue following, code audit, persistent reconciliation, and general code the board. the universally adored open source appropriated rendition control framework.
#### 2: GitLab
It's completely open source. You can have your code directly on GitLab's site much like you would on GitHub, yet you can likewise decide to self-have your very own GitLab case individually server and have full power over who approaches everything there and how things are overseen. GitLab practically has highlighted equality with GitHub, and a few people may even say its ceaseless incorporation and testing devices are prevalent. In spite of the fact that the network of engineers on GitLab is unquestionably littler than the one on GitHub,
#### 3: Bitbucket
Bitbucket has been around for a long time. Bitbucket was procured by a bigger partnership (Atlassian) eight years back It's as yet a business stage like GitHub, however, it's a long way from being a startup, and it's on really stable balance, hierarchically. Bitbucket shares the vast majority of the highlights accessible on GitHub and GitLab, in addition to a couple of novel highlights of its own, similar to local help for Mercurial storehouses.
#### 4: SourceForge
The granddaddy of open source code store locales is SourceForge. It used to be that on the off chance that you had an open source venture, SourceForge was the spot to have your code and offer your discharges. It took a short time to move to Git for adaptation control, and it had its very own rash of the business obtaining and re-securing occasions, combined with a couple of tragic packaging choices for a couple of open source ventures. So, SourceForge appears to have recuperated from that point forward, and the site is as yet a spot where many open source extends live.

[read more: comparison of git hosting services](https://www.git-tower.com/blog/git-hosting-services-compared)

### Q: What is git rebase and how is it differnt from git merge?
**A:** Rebasing differs from merging by that it relocates (moves) the commit to a new location, while merging glues two together into 1, but keeps the history. When rebasing a feature branch to main branch, the whole history of the feature branch is moved to main branch, added on top of it, and it becomes a part of that branch visually just extending it - it's 1 straight timeline as a result. When merging a feature branch with main, the history of the feature branch is kept separately, a new commit for the merge is made atop of it and that's where 2 branches meet and go onwards as 1 branch from that point on.

### Q: What is the function of git config?
**A:** It stores the user configuration of git repository, for example the user name and email address or the preferred text editor. User settings in git config can be checked by running the command git config --list in the command terminal.

### Q: What is the function of git diff?
**A:** It compares two objects, for example two versions of a file, one on the remote origin and one with some changes in our local repository.

### Q: How to resolve conflicts in Git?
**A:** A conflict may arise when merging two branches whenever one and the same file has two different changes done to it. Git will then stop the auto merge and return a conflict for us to first solve. You can then remove the conflicting files from the merge using git checkout, open the local file and see the conflict, resolve it and save, add the file to the merge (git add) and commit the solution (git commit with message describing the conflilct solution) and this will be added to the merging commit solving the merge conflict and the merge will then finalise (commit).

### Q: One of your teammates accidentally deleted a branch and has already pushed the changes to the central git repo. There are no other git repos, and none of your other teammates had a local copy. How would you recover this branch?
**A:** I'd use git reflog. There's kind of a hidden history of local repository which also can be accessed, basically every action you perform inside of Git where data is stored and git reflog is the tool to access it. So using git reflog go to the latest commit to this deleted branch and then check it out as a new branch. 

### Q: How to list files changed in a particular commit?
**A:** Git log with -p or --stats or other reporting options, but with only 1 commit id or its hash.

### Q: How to view the commit history of the repository?
**A:** Basically using git log, but there's a lot of modificators that can be used here, such as --pretty, --oneline, --stats, -p, we can print a small report or a bit one, with whole working tree drafted along the listed commits, we can limit by date and by author, by certain file or filetype...

### Q: How to permanently remove a committed file from the repository?
**A:** First remove the file from the commit with git rm and save this change by committing it.

### Q: How do you setup and use SSH authentication to connect with github/remote repository?
**A:** To do SSH setup for git we need to create a .ssh directory in the user's home directory, navigate to it with command terminal and run command ssh-keygen -t rsa -C "(your-email-id)". Here -t is used to specify type of key to create and -C(in upper case only) to provide the comment in this case the email-id. You will then be asked to provide inputs like name of file to store the key (or just press to have it saved as "id_rsa") and provide a passphrase. This creates a file "id_rsa.pub" will be created in ".ssh" directory.
Once that's done, add the SSH key to GitHub (in account settings) - this key will be paired with the machine where SSH key was generated. Paste the contents of "id_rsa.pub" to add the key and run the command "ssh -T git@github.com" in your termindal to establish an SSH connection with GitHub.
