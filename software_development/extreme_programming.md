# eXtreme Programming
## Overview
Extreme Programming (XP) is a process for software development. Like other agile methods, it focuses on tight feedback loops, both between the developers and the code and and between the developers and the customer. This is intended to keep everyone's expectations accurate and avoid unpleasant surprises.
## Development Process
### Initial Setup
A couple of things have to happen before the customer and the developers have their first meeting.
#### User Stories
The customer has to write a first draft of a set of *user stories*. (This is currently done in a shared Google Doc.) Each story describes some desired capability of the software. For example:

| Duck Detonation |
|-|
|When the user clicks on the Detonate button, the duck explodes.|

Stories should be relatively small and testable *by the customer*. They should avoid any technical details about *how* a feature will be implemented.

Stories will be modified, added, and discarded as the project proceeds. Nothing is etched in stone.
#### Setting Up a GitHub Repository
**One developer** should [create a new GitHub repository](setting_up_githib.md). The others should then clone it to their local machines.
### Iteration
Development proceeds in a series of iterations (known in some other agile methods as sprints). For the main Software Development project, each iteration lasts two weeks.

Each iteration consists of four stages:
1. Customer meeting
1. Planning
1. Coding
1. Delivery
#### Customer Meeting
During the customer meeting, we play the "planning game". Here the developers determine the *cost* of stories and the customer determines the *value* of stories. Specifically:
1. The customer writes stories. They may modify, add, or discard old stories. The developers and the customer should discuss these stories to make sure that everyone understands what is needed. The customer also indicates, very roughly, which stories should be tackled first.
1. The developers estimate how long each story (or at least those stories in the "tackle next" category) will take. Each story is given a rating from 1 to 3 units of difficulty. As a rough approximation, 1 means that a pair of developers could complete the story in under an hour, 3 means that it would take the entire iteration, and 2 is somewhere in between. If a story seems so difficult that it cannot be accomplished in one iteration, it should be broken down into smaller stories. Note that the estimate should be for completing that story *independent of any other stories*; the developers don't yet know in what order stories will be tackled.
1. The customer is given a budget to choose stories. For the first iteration, this will be 3 units times the number of developer pairs; for later iterations, it will be based on the number of units the team has completed over each of the last few iterations. Given this budget, the customer chooses which stories they want the developers to work on first.
During or after the customer meeting, the developers should copy the user story titles into the GitHub repository as issues.
#### Planning
The developers now meet to do a small amount of planning.
1. Come up with a simple overall design. This is just about the high-level organization of the system; it shouldn't get into details like what data structures are used inside particular classes.
1. Decide who will pair with whom. (If the team has an odd number of developers, one "pair" will have three people.) The pairs should change each iteration. This serves to propagate knowledge (about programming, our tools, and our system) around the group. It also prevents creating indispensable developers who are the only ones able to work with some part of the system; the project may grind to a halt if such a person calls in sick or is hit by a meteor.
1. Each pair now chooses **one** story, claims it on GitHub, and starts work on it. If a task involves detailed knowledge (e.g., of some API or part of our system) that some developers gained in a previous iteration, it is best handled by a pair that consists of one knowledgeable person and one new person.
#### Coding
#### Delivery
## Additional Resources
### Online
- [Extreme Programming: A gentle introduction](http://www.extremeprogramming.org/)
- [The Agile Manifesto](https://agilemanifesto.org/)
- [Extreme Programming: Values, Principles, and Practices](https://www.altexsoft.com/blog/business/extreme-programming-values-principles-and-practices/)
- GitHub guide: [Mastering Issues](https://guides.github.com/features/issues/)
- [GitHub Issues Can be Agile if You To it Right](https://zube.io/blog/agile-project-management-workflow-for-github-issues/)
### Print
- Christensen, *Flexible, Reliable Software Using Patterns and Agile Development*, Chapter 1
- Steinberg and Palmer, *Extreme Software Engineering: A Hands-On Approach*
## Questions
## Answers
