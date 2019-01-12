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
A *repository* is a set of snapshots of your files. (Git is actually clever enough to save space by only storing the *differences* between these snapshots, but you don't have to think about that.)

First create a directory and put a simple file in it -- say, `file.txt`.

Now, within that directory, initialize the repository with this command:
```
git init
```
To see the status of the repository, use this command:
```
git status
```
The output tells you that you are on the master branch (more about branches later), you haven't made any *commits* (snapshots), and your file is still untracked. You have to explicitly tell git which files to keep track of. There are often files you *don't* want to put under version control, such as compiled programs and huge data files.

To add a file to version control:
```
git add file.txt
```
To make your first commit:
```
git commit -m 'Initial project version'
```
The part at the end is the commit message, explaining what you changed.

If you check the status again, you will see that there is now "nothing to commit" -- your current workspace of files matches the most recent commit. In general, working with git is a cycle of making changes to your files and then committing them.
### Committing
Edit a file. Alternately, create a new file and add it to version control.

Before committing, it's a good habit to always run `git status` to make sure things are in the state you think they're in.

Now commit:
```
git commit -m 'My poem is now twice as long'
```
Check the status again to make sure it worked.
### Viewing Past Commits
## Additional Resources
### Online
### Print
## Questions
## Answers
