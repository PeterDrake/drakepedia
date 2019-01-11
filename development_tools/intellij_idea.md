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
### Creating a Project
1. Open IntelliJ IDEA and click Create New Project.
2. Verify that the Project SDK is not empty (if it is, your Java installation didn't work) and click Next.
3. Check Create project from template and click Java Hello World.
4. Give the project a simple name, like "CS2", and click Finish.

You can click on the little triangles at left to expand directories. Your code goes in the src directory.
### Running a Program
There are several ways to do this:
- With the program file open, click on the green "play" triangle next to the class (or next to the main method) and choose Run.
- Right click on the file within the src directory and select Run.
- Click on the green play triangle near the top center of the window. This runs the last program that was run; that's
*usually* what you want, but it can sometimes give surprising results if you've started editing a different file.
- Hit ctrl-R (with the same caveat).
- Use the Run menu at the top of the screen.
