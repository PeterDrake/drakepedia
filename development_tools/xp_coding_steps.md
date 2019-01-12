# Extreme Programming Coding Steps
## Overview
Congratulations! You're involved in an Extreme Programming project, your team has met with the customer and done initial planning, and now you and your pair programming partner are ready to start coding. This document gives a checklist to go through as you work. (Don't worry, there's still *plenty* of room for creativity and problem-solving.) The navigator should keep this page open and always know where you are in the list.

Don't skip steps! That way lies madness.

Don't spend hours in any one step. Keep moving so that commits and merges are frequent. There are few things less pleasant than merging two branches that haven't communicated with each other in weeks.

Here's an outline of the process:
1. Get the latest version of the code from GitHub
1. Choose a branch
1. Merge from `master`
1. Do actual coding
1. Issue pull request
1. Review code
1. Choose a new task
## Get the Latest Version of the Code from GitHub
### Command Line
```
git pull -all
```
Note that `pull` both fetches the remote versions of all branches and tries to merge them into your local branches. If this results in a merge conflict, you'll have to resolve it.
### IntelliJ IDEA
`VCS` | `Git` | `Pull`. In the window that pops up, click on the two-circling-arrows icon on the right before clicking `Pull` so you'll get any branches that others created.
## Choose a Branch
### Command Line
If you're creating a new branch:
```
git checout -b branchname
```
If you're just checking out an existing branch, leave out the `-b`.
### IntelliJ IDEA
`VCS` | `Git` | `Branches...`. Select either `New Branch` or the name of the branch you want to check out.
## Merge From master
You want to make sure that everyone *else's* changes will work with your code before your share your work.
### Command Line
```
git merge master
```
### IntelliJ IDEA
`VCS` | `Git` | `Merge Changes...`. Make sure you're on the branch you think you're on, check `master`, and click `Merge`.
## Do Actual Coding
If you're about to issue a pull request, skip this entire step.

1. Unless you're just refactoring, write one or more new unit tests. Run the tests to make sure they fail.
1. Commit your changes.
1. Write/edit code until it passes all tests.
1. Commit your changes.

You've now added some new functionality! You can now either repeat this step or go back the beginning. You would go back to the beginning if either:
- you have completed a task and are ready to share it with the rest of the team, or
- others have merged some changes into `master` and you want to have access to them.

One or the other of these things should happen often!
### Committing From the Command Line
```
git commit -am 'Your commit message here'
```
### Committing From IntelliJ IDEA
`command-k`. Choose `Commit and Push` at the lower right.
## Issue Pull Request
