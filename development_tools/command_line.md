# Command Line
## Overview
While I generally prefer to work in an integrated development environment like [IntelliJ IDEA](intellij_idea.md), it's certainly possible to develop Java programs from the command line.

You must first have the [Java Development Kit](https://www.oracle.com/technetwork/java/javase/downloads/index.html) installed
on your machine. You can verify that this is working by typing `javac -version` on your command line.

The simple program below should be saved in a file called `Hello.java`. You can use any simple text editor, such as
[Emacs](https://www.gnu.org/software/emacs/) (which comes pre-installed on most \*nix-based systems, including macOS),
[Vim](https://www.vim.org/) (ditto), or [Sublime Text](https://www.sublimetext.com/). Be careful not to use a word processor
such as Microsoft Word, Notepad, or TextEdit, which will add extraneous formatting information to the file. Note that Java is
case-sensitive and that it insists that the name of the class match the name of the file.
```java
public class Hello {

    public static void main(String[] args) {
        System.out.println("Hello World!");
    }

}
```
To compile the program, run this command:
```
javac Hello.java
```
This creates a compiled class file called `Hello.class`. To run the program:
```
java Hello
```
## Additional Resources
### Online
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 1.1](https://introcs.cs.princeton.edu/java/11hello/)
- Oracle's *Essentials of the Java Programming Language*, [Lesson 1](https://www.oracle.com/technetwork/java/compile-136656.html)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 1.1
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Sections 2.1-2.2
## Questions
1. :star: What command is used to *compile* a Java program from the command line?
1. :star: What command is used to *run* a Java program from the command line?
1. :star::star: A Java program begins with the line `public class Dog {`. What must the file containing this program be called?
## Answers
1. `javac`
1. `java`
1. `Dog.java`
