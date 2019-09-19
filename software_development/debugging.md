# Debugging
## Overview

Most of your programming time is probably spent debugging. There are several things you can do to reduce this time and produce more correct software.

### Preventing Bugs

The best [bug](https://codingblonde.com/2015-08-computer-bug-real-insect/) is the one that never happens. To minimize the number of bugs, keep your code clear and organized. Use well-encapsulated classes and methods so that you can think about one thing at a time. The more you have to keep in your head, the more mistakes you will make.

Give variables and methods names that clearly explain their purpose. For example, if you have a method to check the parity (oddness or evenness) of a number, don't call it `checkParity`; that requires you to remember if returning true means odd or even. Instead, call it `isEven`.

### Noticing Problems

This almost goes without saying, but you can't fix a bug until you realize there is a problem. If you have no way of knowing whether your program is working correctly, debugging it is hopeless.

Design your program to [fail fast](https://en.wikipedia.org/wiki/Fail-fast), so you find out about errors as soon as possible.

### Reproducing Problems

Before you can fix a problem, you must be able to reliably reproduce it. (This is what makes nondeterministic bugs, which only appear some of the time, particularly heinous.) Figure out which input or other conditions cause the problem to occur.

After you can do this manually, encode the problem into a [JUnit test](testing.md#junit) that fails with the buggy code. This way, you'll know when you've fixed the bug.

If you're using [test-driven development](testing.md#test-driven-development), you may have already handled preventing bugs, noticing the problem, and reproducing the problem. Of course, not all problems can be foreseen, but anything you can do to make the debugging process easier is worthwhile.

Now that you can reproduce the problem, several approaches are available for hunting down the bug.
### Debugging
#### Viewing Error Messages
Java's error messages are usually quite helpful (compared to other programming languages). When an exception or error occurs, you are told the type of problem (e.g., `NullPointerException`) and given a stack trace of where it occurred. Go through the stack trace line by line from the top until you find a line that is in your code (as opposed to in a standard library, which is unlikely to contain a bug). Click on the line number to go there in your code. What, on this line, could have caused that exception?

For example, if you have a `NullPointerException` on a line like

```java
foo.bar().quux(baz.zorch(3));
```

Then either `foo` is `null`, `foo.bar()` returns `null`, or `baz` is `null`.
#### Using `println` Statements
This is a classic technique that should work in just about any programming environment. The goal is to find the place where what the program is actually doing differs from what you think it is doing.

Find a sequence of statements (possibly spread across several methods) within which you are pretty sure the bug occurs. (In the limit, this is the entire program.) Put in a `println` statement about halfway through this sequence that demonstrates that (a) the program reached this point, and (b) the variable in question has the correct value.

Run the program. If everything is working correctly at the `println`, the problem must occur after that line. If not, it must occur before then. Now you can put a `println` halfway through the remaining suspicious code, and so on, until you find the culprit.

This is analogous to the binary search algorithm.
#### Using a Debugger

An automatic *debugger* like the one built into [IntelliJ IDEA](../development_tools/intellij_idea.md) does not, sadly, automatically remove bugs. It does allow you to step through your program in great detail and inspect the values of variables at any point.

To use a debugger, set one or more *breakpoints*, typically by clicking to the left of the line of code. Run the program in debug mode. It will run until it reaches the breakpoint and then pause, showing the state of the call stack and values of the variables. If you tell the debugger to continue, it will resume running until it reaches another breakpoint or the end of the program.

It is also possible to set up fancier breakpoints that pause the program only under certain conditions, whenever a particular variable is accessed, whenever a particular exception is thrown, etc.

## Resources
- IntelliJ documentation:
    - [Debugging Your First Java Application](https://www.jetbrains.com/help/idea/debugging-your-first-java-application.html)
    - [Breakpoints](https://www.jetbrains.com/help/idea/using-breakpoints.html)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 7.6
## Questions
1. :star: What does a breakpoint do?
1. :star::star: When is it better to use `println` statements versus a debugger?
## Answers
1. When you run a program in debugging mode, the debugger pauses whenever it reaches a breakpoint. You can then inspect the values of variables.
1. Usually a debugger is preferable because you can set a breakpoint that displays all variables with a single mouse click (and remove it just as easily). You might use `println` statements if you don't have a debugger available or if you want to quickly inspect one variable at many points during the run (such as every pass through a loop that runs a hundred times).
