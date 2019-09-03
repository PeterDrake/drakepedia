# stdlib
## Overview
The Princeton Standard Library, also known as stdlib, is a collection of Java classes developed by Robert Sedgewick and Kevin Wayne to make certain tasks easier. Installation is [straightforward](../development_tools/intellij_idea.md#installing-stdlib).
## Writing to the Console
The standard Java

```java
System.out.println("Hello!");
```

is replaced with the slightly more concise:

```java
StdOut.println("Hello!");
```

## Reading From the Console

To read a line of text from the console and store it in a String `s`:

```java
String s = StdIn.readLine();
```

If you search for the standard Java way of doing this, you'll probably find an overly complicated procedure involving a Scanner object.

You can ask for particular types of data:

```java
int n = StdIn.readInt();
```

Two things to watch out for:

- When your program gets to any sort of read, it will stop until the user enters appropriate input. To avoid confusing your user, print some sort of prompt first.
- If you use something like `readInt`, only the next available number (and any whitespace before it) is consumed. The rest of the line remains in the input stream waiting to be read. Thus, if the user types `23` on a line by itself, a call to `readInt` will return 23 and a subsequent call to `readLine` will return an empty String. You can avoid this by either (a) not mixing the two or (b) calling `readLine` to flush out the rest of the line after reading a number.

## Interacting With Files

If you define

```java
Out out = new Out("junk.txt");
```

and then

```java
out.println("Hello!");
```

then `Hello!` will be written to the file `junk.txt`. Each time you run your program it will replace the old contents of the file.

Similarly, if you define

```java
In in = new In("junk.txt");
```

then each

```java
String s = in.readLine();
```

will read another line of text from the file. You'll often want to do this in a [loop](../control_structures/loops.md), using `in.isEmpty()` to detect when you've reached the end of the file.
## Random Numbers
You can generate a random double that is at least 0.0 and less than 1.0 with:

```java
double x = StdRandom.uniform();
```

To generate a random integer that is at least 0 and less than 10:

```java
int n = StdRandom.uniform(10);
```

## Graphics
While it would not be a good choice for building a complicated user interface will all kinds of buttons, sliders, and text fields, stdlib is *much* easier to use than the standard javax.swing for creating simple diagrams, animations, and games.

A wide variety of methods are available in the StdDraw class. For example,

```java
StdDraw.circle(0.5, 0.75, 0.2);
```

creates this picture:
![A circle, of radius 0.2, centered at x equals 0.5 and y = 0.75](stddraw_circle.png)

The three arguments in the case are the *x* coordinate, the *y* coordinate, and the radius.

*x* ranges from 0.0 on the left to 1.0 on the right; *y* ranges from 0.0 at the bottom to 1.0 at the top. This is what you're probably used to from plotting curves in mathematics, but differs from some other computer graphics systems (which measure y from the top down).

### Double Buffering

StdDraw has two modes. The default mode, designed to let people get started as quickly as possible, draws things on the screen as soon as commands are executed.

The other mode stores up the various draw commands and doesn't show anything until there is a call to `StdDraw.show()`. This is called *double buffering*. If you are drawing many things or doing any sort of animation, this will avoid an ugly flickering effect. To enter this mode,

```java
StdDraw.enableDoubleBuffering();
```
once at the beginning of your program.
### Animation
If you are doing animation in a loop, resist the temptation to just change one part of the screen; that way lies confusion and despair. Instead, start each pass through your loop with
```java
StdDraw.clear();
```
to clear the window and end each pass with
```java
StdDraw.show();
```
### Mouse and Keyboard Input
## Resources

## Questions
1. :star::star: Why aren't we using real Java?
1. :star::star: How would you generate the result of rolling a fair, six-sided die?
1. :star::star: Why doesn't the code below draw anything?
    ```java
    StdDraw.enableDoubleBuffering();
    StdDraw.filledRectangle(0.5, 0.5, 0.1, 0.3);
    ```
## Answers
1. This is real Java; nothing about the language has changed. We are simply using a library of code that someone else has written so that we don't have to write a bunch of tedious code that isn't relevant to the topics we're studying.
1.
    ```java
    int roll = StdRandom.uniform(6) + 1;
    ```
    or
    ```java
    int roll = StdRandom.uniform(1, 7);
    ```
1. It must be followed by `StdDraw.show();`.
