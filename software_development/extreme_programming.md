# eXtreme Programming
## Overview
eXtreme Programming (XP) is a process for software development. Like other agile methods, it focuses on tight feedback loops, both between the developers and the code and and between the developers and the customer. This is intended to keep everyone's expectations accurate and avoid unpleasant surprises.
## Development Process
### Initial Setup
A couple of things have to happen before the customer and the developers have their first meeting.
#### User Stories
The customer has to write a set of *user stories*. (This is currently done in a shared Google Doc.) Each story describes some desired capability of the software. For example:

| Save File |
|-|
|The user can save the state of the file they are editing.|

Stories should be relatively small and testable *by the customer*. They should avoid any technical details about *how* a feature will be implemented.

Stories will be modified, added, and discarded as the project proceeds. Nothing is etched in stone.
#### Setting Up a GitHub Repository
**One developer** should:
1. Create a local repository
   1. Create a new project and put it under version control. In IntelliJ IDEA, this means creating a new project and then selecting `VCS` | `Enable Version Control Integration` | `Git`.
   1. Create a `.gitignore` file to tell git which files to ignore. For a Java project, a reasonable file is:
   ```
   .DS_Store
   out/
   *.class
   *~
   *.jar
   ```
   1. Add all remaining files to version control. In IntelliJ IDEA, open the version control tool window (`command-9`), select the files under `Unversioned Files`, right click, and select `Add to VCS`.
1. Commit to the local repository. In IntelliJ IDEA, click on the project at the top of the Project window (so that all files are selected) and hit `command-k`.
1. Create a repository on GitHub
   1. Log into github.com.
   1. Click on the green `New repository` button on the right.
   1. Give the new repository the same name as the IntelliJ IDEA project.
   1. Select `Private`; do not initialize with a README.
   1. Click `Create repository`.
   1. Copy the https URL to the clipboard.
1. Push to the remote repository
In IntelliJ IDEA, this means selecting `VCS` | `Git` | `Push`, clicking on `Define remote`, and pasting the https URL.
1. Add other team members as collaborators
This is done on the GitHub website, from the repository: `Settings` | `Collaborators`  
### Iteration
#### Customer Meeting
#### Planning
#### Coding
#### Delivery
## Additional Resources
### Online
- [Extreme Programming: A gentle introduction](http://www.extremeprogramming.org/)
- [The Agile Manifesto](https://agilemanifesto.org/)
- GitHub guide: [Mastering Issues](https://guides.github.com/features/issues/)
- [GitHub Issues Can be Agile if You To it Right](https://zube.io/blog/agile-project-management-workflow-for-github-issues/)
### Print
- Christensen, *Flexible, Reliable Software Using Patterns and Agile Development*, Chapter 1
- Steinberg and Palmer, *Extreme Software Engineering: A Hands-On Approach*
## Questions
## Answers
