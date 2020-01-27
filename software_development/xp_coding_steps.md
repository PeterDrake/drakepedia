# Extreme Programming Coding Steps
## Overview
Congratulations! You're involved in an Extreme Programming project, your team has met with the customer and done initial planning, and now you and your pair programming partner are ready to start coding. This document gives a checklist to go through as you work. (Don't worry, there's still *plenty* of room for creativity and problem-solving.)

Don't skip steps! That way lies disaster.

Don't spend hours in any one step. Keep moving so that commits and merges are frequent. There are few things less pleasant than merging two branches that haven't communicated with each other in weeks.

Here's an outline of the process:

1. [Choose a task](#1-choose-a-task)
    1. [Choose a story](#1i-choose-a-story)
    1. [Choose a task](#1ii-choose-a-task)
1. [Get the latest version of your team's work](#-2-get-the-latest-version-of-your-teams-work)
    1. Make sure you are in a clean state
    1. Pull everything
    1. Check out your branch
    1. Merge from master
1. Write/edit code
    1. Make sure you are in a clean state and on the right branch
    1. Unless you're just refactoring, write and fail new unit tests
    1. Commit the tests
    1. Write/edit code
    1. Run tests; if they fail, go back to (3.iii)
    1. Commit locally
    1. Go back to (3.ii) unless you've finished a task or it's almost the end of the session
1. Share your work with your team
    1. Get the latest version of your team's work
    1. Issue a pull request
    1. Review code
    1. If you've finished your task, indicate your progress on Trello and go back to (1)
    1. If it's not the end of the session, go back to (2)

**The navigator should keep this page open and always know where you are in the checklist.**

## 1 Choose a task
### 1.i Choose a story
On Trello, you and your partner should be attached to a card in the In Progress column. If you're here because you just finished a story, pick a new one from the current iteration in the Iterations column; if there aren't any, pick a story from the next iteration. Don't skip ahead to a story that looks easy or interesting; respect the customer's priorities about what to work on next.
### 1.ii Choose a task
If the story has a checklist of tasks in it, pick the next task in the list.

## 2 Get the latest version of your team's work
### 2.i Make sure you are in a clean state
Remember that you must always be in a clean state before trying to do anything else with git or GitHub; failure to do so is a good way to lose your work. If you are *not* in a clean state, you need to either *commit* or (on rare occasions) *throw away your work since the last commit* before proceeding.

#### To check if you are in a clean state

---

##### Command line
```
git status
```

The resulting message tells you what branch you're on if you have changes since the last commit. It should end in

```
nothing to commit, working tree clean
```
##### IntelliJ IDEA
`command-9` (Mac) / `alt-9` (Windows) to open the version control tool window. It should say
```
Default Changelist
```

and nothing else.

The current branch is shown at the lower right, after the word `Git:`.

---

#### To commit

---

##### Command line
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

##### IntelliJ IDEA
To add files to version control:

`command-9` (Mac) / `alt-9` (Windows) to open the version control tool window. Right-click on files to add them to version control.

To commit:

`command-k` (Mac) / `ctrl-k` (Windows). Make sure the right files are checked at the top of the dialog box and that the commit message explains how the program's behavior is different. Choose `Commit` at the lower right.

---

#### To throw away your work since your last commit

**_THIS IS USUALLY NOT WHAT YOU WANT. ONLY DO THIS IF YOU ARE ABSOLUTELY SURE YOU WANT TO THROW AWAY ALL CHANGES SINCE YOUR LAST COMMIT._**

---

##### Command line

```
git reset --hard HEAD
```

##### IntelliJ IDEA

`VCS` | `Git` | `Reset HEAD...`. Choose `Reset Type` `Hard` and click `Reset`.

---

### 2.ii Pull everything

Pulling both fetches the remote versions of all branches and tries to merge them into your local branches. This *shouldn't* result in any merge conflicts. If it does (because you and someone else were committing on the same branch), you'll have to resolve the conflicts.

---

#### Command line

```
git pull -all
```

#### IntelliJ IDEA

`VCS` | `Git` | `Pull`. In the window that pops up, click on the two-circling-arrows icon on the right and check all the branches before clicking `Pull` so you'll get any branches that others have created or updated.

---

### 2.iii Check out your branch

**_YOU SHOULD NEVER DO ANY CODING WHILE ON THE MASTER BRANCH. ALSO, TWO DIFFERENT PAIRS SHOULD NEVER BE WORKING ON THE SAME BRANCH._**

---

##### Command line

If you're creating a new branch:
```
git checkout -b branchname
```
If you're just checking out an existing branch, leave out the `-b`.

##### IntelliJ IDEA

`VCS` | `Git` | `Branches...`. Select either `New Branch` or the name of the branch you want to check out.

---

### 2.iv Merge from master

This step merges all of the changes from the master branch (including work by other members of your team) into your branch.

---

#### Command Line
```
git merge master
```
#### IntelliJ IDEA
`VCS` | `Git` | `Merge Changes...`. Make sure you're on the branch you think you're on, check `master`, and click `Merge`.

---

Make sure that the merge worked. If you get an error message indicating a merge conflict, resolve the conflict by editing the offending files and then committing again. **_Do not do anything else until you have resolved the conflict._**

## 3 Write/edit code
### 3.i Make sure you are in a clean state and on the right branch

This is the same as (2.i), but also make sure the correct branch is showing.

### 3.ii Unless you're just refactoring, write and fail new unit tests

In test-driven development, every change should be either refactoring or trying to pass some test.

### 3.iii Commit the tests

See (2.i) for instructions on committing.

### 3.iv Write/edit code

You'll spend most of your time here ...

### 3.v Run tests; if they fail, go back to (3.iv)

If they pass, bask in the glow of the green bar.

### 3.vi Commit locally

See (2.i) for instructions on committing.

### 3.vii Go back to (3.ii) unless you've finished a task or it's almost the end of the session

You will probably spend most of your time in (3.ii) through (3.vii). This should result in very frequent commits -- *at least* once per hour, ideally even more often. Committing every few minutes is perfectly reasonable.

## 4 Share your work with your team

This should happen several times per session. If you end a session without sharing, your team will have a real problem if you are sick or otherwise unavailable next session.

### 4.i Get the latest version of your team's work

This is exactly the same as step (2).

### 4.ii Issue a pull request

Go to the GitHub website for your project. Choose the branch you're on (using the selector on the left end of the line that has the green `Clone or download` button on the right) and choose `New pull request`.

This tells your team, "Our branch has some new functionality. Let's merge it into master."

### 4.iii Review code

Now find another pair in your team to review your code. You may have to wait a few minutes for them to make their next commit so that they can give you their full attention.

Working with this other pair on GitHub, review the changes you made. Some things to consider:
- Does the new code compile, run, and perform as advertised?
- Are there thorough unit tests?
- Do the tests pass?
- Is the code clean and well-documented?
- Is there any way the code could be improved?

If not everyone is satisfied, go back (3.ii) if you need a new test or (3.iv) otherwise. The pull request remains open.

When everyone is happy, have someone from the other pair enter a review and click on `Merge pull request`. Now your new features have been incorporated into the `master`.

### 4.iv If you've finished your task, indicate your progress on Trello and go back to (1)

Check off the task. If the story is complete, move it to the Done column.

### 4.v If it's not the end of the session, go back to (2)

You have finished something and are now ready to move on to the next thing!



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
