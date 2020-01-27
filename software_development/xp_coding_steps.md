# Extreme Programming Coding Steps
## Overview
Congratulations! You're involved in an Extreme Programming project, your team has met with the customer and done initial planning, and now you and your pair programming partner are ready to start coding. This document gives a checklist to go through as you work. (Don't worry, there's still *plenty* of room for creativity and problem-solving.)

Don't skip steps! That way lies disaster.

Don't spend hours in any one step. Keep moving so that commits and merges are frequent. There are few things less pleasant than merging two branches that haven't communicated with each other in weeks.

Here's an outline of the process:

1. Choose a task
    1. Choose a story
    1. Choose a task
1. Get the latest version of your team's work
    1. Make sure you are in a clean state
    1. Check out master
    1. Pull everything
    1. Check out your branch
    1. Merge from master
1. Write/edit code
    1. Make sure you are in a clean state and on the right branch
    1. Unless you're just refactoring, write and fail new unit tests
    1. Write/edit code
    1. Run tests; if they fail, go back to (iii)
    1. Commit locally
    1. Go back to (i) unless you've finished a task or it's almost the end of the session
1. Make your work available to your team
    1. Get the latest version of your team's work
    1. Issue a pull request
    1. Review code
    1. If you've finished your task, indicate your progress on Trello and go back to (1)
    1. If it's not the end of the session, go back to (2)

**The navigator should keep this page open and always know where you are in the checklist.**

## 1 Choose a task
### Choose a story
On Trello, you and your partner should be attached to a card in the In Progress column. If you're here because you just finished a story, pick a new one from the current iteration in the Iterations column; if there aren't any, pick a story from the next iteration. Don't skip ahead to a story that looks easy or interesting; respect the customer's priorities about what to work on next.
### Choose a task
If the story has a checklist of tasks in it, pick the next task in the list.

## Get the latest version of your team's work
### Make sure you are in a clean state
Remember that you must always be in a clean state before trying to do anything else with git or GitHub; failure to do so is a good way to lose your work.
#### To check if you are in a clean state
##### Command line
```
git status
```

The resulting message tells you what branch you're on if you have changes since the last commit. It should end in

```
nothing to commit, working tree clean
```
##### Intellij IDEA
`command-9` (Mac) / `alt-9` (Windows) to open the version control tool window. It should say
```
Default Changelist
```
and nothing else.

#### To commit
#### To throw away your work since your last commit


To get into a clean state, either commit or (if you're absolutely sure you want to throw away all changes since the last commit) git reset --hard HEAD.

### Check out master
### Pull everything
### Check out your branch
### Merge from master

## Write/edit code
### Make sure you are in a clean state and on the right branch
### Unless you're just refactoring, write and fail new unit tests
### Write/edit code
### Run tests; if they fail, go back to (iii)
### Commit locally
### Go back to (i) unless you've finished a task or it's almost the end of the session
    
## Make your work available to your team
### Get the latest version of your team's work
### Issue a pull request
### Review code
### If you've finished your task, indicate your progress on Trello and go back to (1)
### If it's not the end of the session, go back to (2)


UNDER CONSTRUCTION -- CHECK BACK TOMORROW




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
git checkout -b branchname
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
1. Add any new files to version control and commit your changes.
1. Write/edit code until it passes all tests.
1. Add any new files to version control and commit your changes.

Remember that you must **always** be in a clean state before trying to do anything else with git or GitHub; failure to do so  is a good way to lose your work. To get into a clean state, either commit or (if you're **absolutely sure you want to throw away all changes since the last commit**) `git reset --hard HEAD`.

You've now added some new functionality! You can now either repeat this step or go back to the beginning. You would go back to the beginning if either:
- you have completed a task and are ready to share it with the rest of the team, or
- others have merged some changes into `master` and you want to have access to them.

One or the other of these things should happen often!
### Committing From the Command Line
To add a new file to version control:
```
git add yourfile
```

To commit:
```
git commit -am 'Your commit message here'
```

You should also push your code up to GitHub:
```
git push
```

### Committing From IntelliJ IDEA
To add files to version control:

`command-9` (Mac) / `alt-9` (Windows) to open the version control tool window. Right-click on files to add them to version control.

To commit:

`command-k` (Mac) / `ctrl-k` (Windows). Choose `Commit and Push` at the lower right.
## Issue Pull Request
Pull the latest version of the code and then merge `master` into your branch. Once any merge conflicts have been resolved, push the resulting commit.

Now you're ready to share your code with the rest of your team!

1. Go to GitHub.
1. Navigate to your repository and the branch you've been working on.
1. Click on `New pull request`.
1. Set `base` to `master` and `compare` to your branch.
1. Click on `Create pull request`.
## Review Code
Now find another pair in your team to review your code. You may have to wait a few minutes for them to make their next commit so that they can give you their full attention.

Working with this other pair on GitHub, review the changes you made. Some things to consider:
- Does the new code compile, run, and perform as advertised?
- Are there thorough unit tests?
- Is the code clean and well-documented?
- Is there any way the code could be improved?

If not everyone is satisfied, go back to the beginning and make improvements. The pull request remains open.

When everyone is happy, have someone click on `Merge pull request`. Now your new features have been incorporated into the `master`, so everyone else will get them the next time they pull the latest code and merge from `master`.

Check off the task in Trello, or (if you've finished an entire story) move the story to the Done column.

## Choose a New Task
Choose a new task to work on. Often this will be the next task in the same story, but if you've finished an entire story you can pick, from the unclaimed stories, the one that has the highest priority as set by the customer. In that case, attach your names to the card and move it to the In Progress column.
