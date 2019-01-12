# Extreme Programming Coding Steps
## Overview
Congratulations! You're involved in an Extreme Programming project, your team has met with the customer and done initial planning, and now you and your pair programming partner are ready to start coding. This document gives a checklist to go through as you work. (Don't worry, there's still *plenty* of room for creativity and problem-solving.) The navigator should keep this page open and always know where you are in the list.

Don't spend hours in any one step. Keep moving so that commits and merges are frequent. There are few things less pleasant than merging two branches that haven't communicated with each other in weeks.

Here's an outline of the process:
1. Get the latest version of the code from GitHub
1. Choose a branch
1. Merge from `master`
1. Actual coding:
   1. Write unit tests
   1. Fail tests (or go back and fix the tests)
   1. Write code
   1. Pass tests (or go back and fix the code)
   1. Commit
   1. If you haven't completed a task, go back to step 1 or 4.
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
You want to 
