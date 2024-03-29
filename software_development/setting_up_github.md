# Setting Up a GitHub Repository
These are my notes on setting up a GitHub repository for a new project using IntelliJ IDEA or PyCharm. I generally do this myself for research or Software Development projects. For the moment, I give instructions for IntelliJ IDEA and assume things work similarly for PyCharm.
## Create Project in IDE
I describe this [elsewhere](../development_tools/intellij_idea.md).

Optionally, set up a test directory and a sample class and test.

## Put Project Under Local Version Control
`VCS` | `Enable Version Control Integration`. Select Git and click `OK`.
## Set Up .gitignore
1. `File` | `New` | `File`, `.gitignore`, add to version control when asked.
1. Give it the contents below.
   ```
   ## This file tells git what NOT to include in version control

   # General JetBrains configuration information
   .idea/
   *.ipr
   *.iml

   # IntelliJ / Java information
   out/
   *.class

   # PyCharm / Python information
   venv/
   __pycache__/
   *.py[cod]
   *$py.class

   # Automatic backups created by Emacs
   *~

   # Hidden files used by macOS to indicate directory display details, e.g., icon positions
   .DS_Store

   # Sources I consulted in creating this file:
   # https://github.com/github/gitignore/blob/master/Global/JetBrains.gitignore
   # https://github.com/github/gitignore/blob/master/Python.gitignore

   ```
   
1. Add all remaining files to version control.
   1. `command-9` to open version control tool window.
   1. Select files under `Unversioned Files`.
   1. Right click and select `Add to VCS`.
1. Click on the project at the top so all files are select and commit with `command-k`.

## Create Repository on GitHub
1. Log into github.com.
1. Click on the green `New repository` button on the right.
1. Give the new repository the same name as the IntelliJ IDEA project.
1. Select `Private`; do not initialize with a README.
1. Click `Create repository`.
1. Copy the https URL to the clipboard.
## Push to the Remote Repository
1. `VCS` | `Git` | `Push`.
1. Clicking on `Define remote`.
1. Paste https URL.
1. `Push`.
## Protect the main Branch
On GitHub, in `Settings` | `Branches`, add a rule to the `main` branch that requires a pull request before merging. This prevents anyone from accidentally pushing to `main`.
## Add other team members as collaborators
On the GitHub website, from the repository: `Settings` | `Collaborators`.
## References
- [Set up a Git repository](https://www.jetbrains.com/help/idea/set-up-a-git-repository.html)
- [Practicing with IntelliJ and Git](https://gist.github.com/bgun/c7447ab0906517221b6b)
