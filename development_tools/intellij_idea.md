# IntelliJ IDEA
## Overview
Starting in CS2, I like to use IntelliJ IDEA, which is an Integrated Development Environment (IDE). This means that several
tools that would be separate command-line applications (editor, compiler, debugger) are combined into a single program.
This saves time invoking different programs and allows various nice features, such as underlining of compilation errors
in the editor.

I've chosen IntelliJ IDEA because it is:
- widely used in industry,
- free and platform-independent, and
- nearly identical to PyCharm (for Python) and Android Studio (for Android applications), so learning either of these should
easy for someone who knows their way around IDEA.
## Setup
### Downloading
Note that you'll have to [install Java](development_tools/command_line.md) first.

You can download the [Community Edition](https://www.jetbrains.com/idea/download/) for free. You can also get the Ultimate
Edition for free as a student by [filling out a form](https://www.jetbrains.com/student/), but there's no good reason
to jump through this extra hoop.

When the installer presents the option, it wouldn't hurt to install the IDE Features Trainer.
### Creating a Project
1. Open IntelliJ IDEA and click `Create New Project`.
1. Verify that the Project SDK is not empty (if it is, your Java installation didn't work) and click `Next`.
1. Check `Create project` from template and click Java `Hello World`.
1. Give the project a simple name, like "CS2", and click `Finish`.

You can click on the little triangles at left to expand directories. Your code goes in the `src` directory.
### Running a Program
There are several ways to do this:
- With the program file open, click on the green "play" triangle next to the class (or next to the main method) and choose `Run`.
- Right click on the file within the src directory and select `Run`.
- Click on the green play triangle near the top center of the window. This runs the last program that was run; that's
*usually* what you want, but it can sometimes give surprising results if you've started editing a different file.
- Hit `ctrl-R` (with the same caveat).
- Use the `Run` menu at the top of the screen.
### Installing stdlib
1. Download the file stdlib.jar from [Sedgewick & Wayne's website](https://introcs.cs.princeton.edu/java/stdlib/). (The link is right under the table.)
1. Drag and drop the file into your project. You'll want to drop into onto the project folder, just below the word Project
at the upper left of the IntelliJ IDEA window.
1. Right click on the file and select `Add as library`.
## Using IntelliJ IDEA
The information below is enough to let you write and run programs. Everything else is just gravy, but there is a *lot* of
delicious gravy to be had. My general advice is to keep an eye out for anything that seems tedious and then ask if there's
a better way; often there is a way to get the IDE to do the boring work for you.
### Creating a Program
Right click on the src directory and select `New` | `Java Class`.
### Saving a Program
You don't have to do anything! IntelliJ IDEA automatically saves every few seconds.
### A Few Neat Tricks
#### Autocomplete
If you type part of something, IntelliJ IDEA pops up a menu of ways that you might want to complete it. It's practically multiple-choice programming! You can navigate through this menu with arrow keys and hit `enter` to pick the one you want (or just hit 'tab' to accept the first one). Note that while IntelliJ's first suggestion is *often* the right one, sometimes it isn't.

There are also a number of live templates that generate common code, such as `sout` to generate a `System.out.println` statement.
#### Documentation
To see the documentation for a class or method, put your cursor in the word and hit `ctrl-j'. It's faster than searching the web!
#### Renaming
Suppose you want to rename one of your variables or methods. Using a regular editor, this would be tedious and error-prone because you'd have to find all of the places where you used that name. With an IDE, it's much easier.

Put your cursor in the name you want to change. Right click and choose `Refactor` | `Rename`. Now edit the name and hit `enter`. Boom! IntelliJ IDEA changes the name here and everywhere else it is used, *even in other files*!
### Tool Windows
In addition to the main panel where you're editing code, IntelliJ IDEA has several tool windows. You can see a list of them in the `View` menu. You can turn them on or off from that menu or with the indicated hotkeys. You can also drag the borders between them to resize them.

The tool windows you're likely to use most often are:
- Project, which gives you an overview of all of your files.
- Run, which shows the console output (if any) for the current program.
- Structure, which shows the methods in your current class in alphabetical order. No more scrolling through the code!
## Additional Resources
### Online
- You can get a list of hotkeys from the `Help` menu (`Keymap Reference`).
- If you installed the Features Trainer, there is a `Learn` option on the left side of the IntelliJ window; this links to several tutorials. (If you missed that during installation, go to `IntelliJ IDEA` \ `Preferences` | `Plugins` and install `IDE Features Trainer`.
- [JetBrains tutorials](https://www.jetbrains.com/idea/documentation/)
## Questions
## Answers
