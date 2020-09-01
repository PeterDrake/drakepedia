# IntelliJ IDEA
## Overview
Starting in CS2, I like to use IntelliJ IDEA, which is an Integrated Development Environment (IDE). This means that several
tools that would be separate command-line applications (editor, compiler, debugger) are combined into a single program.
This saves time invoking different programs and allows various nice features, such as underlining of compilation errors
in the editor.

I've chosen this IDE (which I'll just call IntelliJ henceforth) because it is:
- widely used in industry,
- free and platform-independent, and
- nearly identical in design to PyCharm (for Python), Android Studio (for Android applications), and Rider (for C#, which is used with the Unity game development engine) so learning any of these should easy for someone who knows their way around IntelliJ.
## Setup
### Downloading
You'll have to install the [Java Development Kit](command_line.md) first.

You can download the [Community Edition](https://www.jetbrains.com/idea/download/) of IntelliJ for free. You can also get the Ultimate
Edition for free as a student by [filling out a form](https://www.jetbrains.com/student/), but there's no good reason
to jump through this extra hoop.

When the installer presents the option, it wouldn't hurt to install the IDE Features Trainer.
### Creating a Project
1. Open IntelliJ and click `Create New Project`.
1. Verify that the Project SDK is version 11 (ask for help if it isn't) and click `Next`.
1. Check `Create project from template` and click `Next`.
1. Give the project a simple name, like "CS2". Make sure the `Base package` field is empty. Click `Finish`.
1. For testing purposes, modify the program that was created to look exactly like this:
    ```java
    public class Main {

        public static void main(String[] args) {
	          System.out.println("Hello, world!");
        }
        
    }
    ```

You can click on the little triangles at left to expand directories. Your code goes in the `src` directory.
### Running a Program
There are several ways to do this:
- With the program file open, click on the green "play" triangle next to the class (or next to the main method) and choose `Run`.
- Right click on the file within the `src` directory and select `Run`.
- Click on the green play triangle near the top center of the window. This runs the last program that was run; that's
*usually* what you want, but it can sometimes give surprising results if you've started editing a different file.
- Hit `ctrl-R` (Mac) / `shift-F10` (Windows), with the same caveat.
- Use the `Run` menu at the top of the screen.
### Installing [stdlib](../libraries/stdlib.md)
1. Download the file stdlib.jar from [Sedgewick & Wayne's website](https://introcs.cs.princeton.edu/java/stdlib/). (The link is right under the table. If you are in CS 383 Algorithm Design and Analysis, you will instead want the file algs4.jar, linked at the bottom of that page.)
1. Drag and drop the file into your project. You'll want to drop into onto the project folder, just below the word Project
at the upper left of the IntelliJ window.
1. Right click on the file and select `Add as library`.
### Installing JUnit
If you are using [JUnit](../software_development/testing.md), you will also neet to set up IntelliJ to support it.
1. Create a new directory, parallel to `src`, called `test`. Your test classes will go here.
1. Right click on this directory and choose `Mark Directory as` | `Test Sources Root`.
1. In a non-test class, place the cursor inside the name of the class (in the line `public class NameOfClass`).
1. Hit `alt-enter` and select `Create Test`.
1. In the dialog window that appears, choose `JUnit5` for the testing library. If there is a `Fix` button just below this, click it and click `OK` the additional dialog window that appears.
1. If you actually want to create a new test class now, check `setup/@Before` and any particular methods you want to test, then click `OK`. If not, click `Cancel`. 
## Using IntelliJ
The information below is enough to let you write and run programs. Everything else is just gravy, but there is a *lot* of
delicious gravy to be had. My general advice is to keep an eye out for anything that seems tedious and then ask if there's
a better way; often there is a way to get the IDE to do the boring work for you. Don't get hung up on memorizing all of the
options, which would be impossible; just learn the features you use often and be vaguely aware of the features you use occasionally (so you can look them up when you need them).
### Creating a Program
Right click on the `src` directory and select `New` | `Java Class`.
### Saving and Compiling a Program
You don't have to do anything! IntelliJ automatically saves every few seconds. It compiles the program (if necessary) every time you run it.
### A Few Neat Tricks
#### Autocomplete
If you type part of something, IntelliJ pops up a menu of ways that you might want to complete it. It's practically multiple-choice programming! You can navigate through this menu with arrow keys and hit `enter` to pick the one you want (or just hit `tab` to accept the first one). Note that while the first suggestion is *often* the right one, sometimes it isn't.

There are also a number of live templates that generate common code, such as `sout` to generate a `System.out.println` statement.
#### Documentation
To see the documentation for a class or method, put your cursor in the name and hit `F1`. It's faster than searching the web!
#### Renaming
Suppose you want to rename one of your variables or methods. Using a regular editor, this would be tedious and error-prone because you'd have to find all of the places where you used that name. With an IDE, it's much easier.

Put your cursor in the name you want to change. Right click and choose `Refactor` | `Rename`. Now edit the name and hit `enter`. Boom! IntelliJ changes the name here and everywhere else it is used, *even in other files*!
### Tool Windows
In addition to the main panel where you're editing code, IntelliJ has several tool windows. You can see a list of them in the `View` menu. You can turn them on or off from that menu or with the indicated hotkeys. You can also drag the borders between them to resize them.

The tool windows you're likely to use most often are:
- Project, which gives you an overview of all of your files.
- Run, which shows the console output (if any) for the current program.
- Structure, which shows the methods in your current class in alphabetical order. No more scrolling through the code!
## Resources
- Detailed installation instructions by Alain Kägi
  - [Linux](https://www.loom.com/share/0cb734dbbc6e4022bb178e14532716d3)
  - [Mac](https://www.loom.com/share/17dc776b62f44a61ad0638de9ed64d2b)
  - [Windows](https://www.loom.com/share/b1c9de8b4855466784c604928f512f96)
- You can get a list of hotkeys from the `Help` menu (`Keymap Reference`). Weirdly, one of the most useful hotkeys (`F1` to get documentation on the method or class under the cursor) isn't on this list. 
- If you installed the Features Trainer, there is a `Learn` option on the left side of the IntelliJ window; this links to several tutorials. (If you missed that during installation, go to `IntelliJ IDEA` | `Preferences` | `Plugins` and install `IDE Features Trainer`.)
- [JetBrains tutorials](https://www.jetbrains.com/idea/documentation/)
## Questions
1. :star: In what directory do program files generally live?
1. :star::star: How do you stop a running program (e.g., one that has gone into an infinite loop)?
1. :star::star::star: You have a data file that your program is going to read. Where should you put that file?
## Answers
1. `src`
1. Click on the red square at the left of the `Run` tool window. Alternately, `Run` | `Stop` (or use the indicated hotkey).
1. Simple answer: put it in your project but not inside `src`. Professional answer: create a directory parallel to `src`; a good name for it is `resources`. Right click on it and select `Mark Directory as` | `Resources Root`.
