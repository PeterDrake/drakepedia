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
## Graphics
## Resources

## Questions
1. :star::star: Why aren't we using real Java?
## Answers
1. This is real Java; nothing about the language has changed. We are simply using a library of code that someone else has written so that we don't have to write a bunch of tedious code that isn't relevant to the topics we're studying.
