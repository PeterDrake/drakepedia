# Git
## Overview
Git is a *version control system*, allowing you to keep track of multiple versions of a piece of software and coordinate changes with other developers. While manually making backup copies and emailing them around is fine for small programs, a tool like git becomes essential for larger projects.
## Setup
### Installation
You can check if git is installed on your system with this command:
```
git --version
```
If it isn't, you can download it from the [git website](https://git-scm.com/).
### Configuration
It's a good idea to run the commands below (with "your name" replaced appropriately) before using git for the first time:
```
git config --global user.name "Your Name"
git config --global user.email yourname@yourdomain.edu
git config --global core.editor emacs
git config --global color.ui true
```
### Creating a Repository
A *repository* (or *repo*) is a set of snapshots of your files.

First create a directory and put a simple file in it -- say, `file.txt`.

Now, within that directory, initialize the repository with this command:
```
git init
```
To see the status of the repository, use this command:
```
git status
```
The output tells you that you are on the master branch (more about branches later), you haven't made any *commits* (snapshots), and your file is still untracked. You have to explicitly tell git which files to keep track of.

To add a file to version control:
```
git add file.txt
```
To make your first commit:
```
git commit -am 'Initial project version'
```
The part at the end is the commit message, explaining what you changed.

If you check the status again, you will see that there is now "nothing to commit" -- your current workspace of files matches the most recent commit. In general, working with git is a cycle of making changes to your files and then committing them.
## Working With Git
### Committing
Edit a file. Alternately, create a new file and add it to version control.

Before committing, it's a good habit to always run `git status` to make sure things are in the state you think they're in.

Now commit:
```
git commit -am 'My poem is now twice as long'
```
Check the status again to make sure it worked.

**You should *always* be in a clean state before trying to do anything else with git.** Usually this means committing. Occasionally you will decide that you instead want to throw away all of your work since the last commit. **If you are *absolutely sure* that you want to do this**, here is the command:
```
git reset --hard HEAD
```
### Working With Past Commits
You can view the history of your repository with this command:
```
git log --pretty=oneline --graph --all
```
Each line represents one commit. It shows the hash (a number that identifies the state of the files) and the commit message. Some additional information like `HEAD -> master` tells you which one is the current commit.

For a example to work with, suppose the output of the log command looks like this:
```
* b3615564012377ecab73e0b693aa7542f84e39df (HEAD -> master) My poem is now twice as long
* 456b316a09a835b22b8822c0f1fd0906c12ae2a5 Initial project version
```
If you want to go back to the previous version, do something like this:
```
git checkout 456b31
```
The hexadecimal number at the end is a prefix of the hash, enough to uniquely identify it. If you now examine your files, you'll see that they're back to the way they were after the first commit!

The newer commit (b36155...) is still in the repository. Once something is in the repository, it's fairly difficult to destroy it. There are git commands that allow you to modify the past, but it's a Bad Idea; you're likely to end up becoming your own grandparent or tearing a hole in the spacetime continuum.

To go back to the newer commit, you could use a similar `checkout` command. A much better idea is to use
```
git checkout master
```
to reattach `HEAD` to the front of the `master` branch. **Never make commits in a detached HEAD state; it could cause you to lose work.**
### Branches
Sometimes you want to do some experimental work on your program without putting it into the `master` branch. This is the time to create another branch. (You should be in a clean state before doing this, but it's okay if you're in a detached HEAD state.) Here's the command:
```
git checkout -b experiment
```
In this example, `experiment` is the name of your new branch. Now that you're on this branch, you can work as normal, modifying files and making commits. If you ever want to switch between branches, just do something like
```
git checkout branchname
```
where `branchname` is the name of the branch you want to switch to (e.g., `master`).

Now suppose your experiment went well and you want to merge the two branches. If you're currently on the `experiment` branch, you can merge any changes from `master` with:
```
git merge master
```
If you commit and merge often, and are a little lucky, merging will succeed automatically. Git is quite clever about this; if the changes on two branches are to different files, or even to different methods within the same file, git can figure out how to keep both sets of changes.

Occasionally, though, it won't be obvious to git how to combine the changes. This is the dreaded *merge conflict*. When this happens, git will open your editor (we specified emacs above) and ask you to resolve the conflict, i.e., edit the files to keep the parts you want. **After you have the files the way you want them, commit again to complete the merge.**
### Remote Repositories
Everything above has been about a local repository on your own machine. This is useful, but the real power of git lies in collaborating with others, using a remote repository stored at someplace like [GitHub](https://github.com/).

Once you have cloned a remote repository to get a local one, you can work along in your local repository. You should avoid working on the `master` branch, but stable code will be merged into it.

Occasionally, you'll want to incorporate the latest changes from the remote `master` branch into the branch you're working on (e.g., `experiment`). First make sure you are in a clean state, then:
```
git checkout master
git pull
git checkout experiment
git merge master
```
The `pull` command brought all the changes from the remote `master` branch into your local `master` branch. You then merged these into your `experiment` branch.

You can now push your branch to the remote branch:
```
git push origin experiment
```
This serves two purposes:
- It stores a remote copy, so you won't lose your work even if your computer is destroyed.
- Once you're confident that your code is woring properly, it enables you to make a *pull request*, asking that your branch be merged into the remote `master` branch.
## Additional Resources
### Online
- [Pro Git](https://git-scm.com/book/en/v2)
- DZone, [Gettig Started with Git Refcard](https://dzone.com/refcardz/getting-started-git?chapter=1)
- [A Visual Git Reference](http://marklodato.github.io/visual-git-guide/index-en.html)
- [git](https://git-scm.com/)
- [GitHub](https://github.com/)
### Print
- Chacon and Straub, *Pro Git*
## Questions
1. :star::star: How often should you commit?
1. :star::star: Where is a local repository stored?
1. :star::star: Does saving all of these copies of files use up a lot of disk space?
1. :star::star: Why would you ever have files in a directory that are not under version control?
## Answers
1. Often -- several times an hour. Part of the point of git is to allow you to go back to a previous commit if you make a mistake, so you want to have many options as to how far to go back.
1. In a hidden directory called `.git` inside the directory where you ran `git init`.
1. No. Git is clever enough to store only the differences between commits.
1. There is no reason to store compiled code, as it can be generated from the source code. Huge, unchanging data files that are available elsewhere are also often left out of version control.
