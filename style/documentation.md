# Documentation
## Overview
> Documentation is a love letter that you write to your future self.
>
> -Damian Conway, *Perl Best Practices*

Code is not just for the computer. It's also read by other people who need to understand how it works, debug it, or add new features. Unless it is thoroughly documented, even your own code will be completely mysterious to you if you haven't looked at it in a few months.

> Writing is thinking. To write well is to think clearly. That's why it's so hard.
>
> -David McCullough, interview with NEH chairman Bruce Cole, *Humanities* 23:4

A second advantage of commenting is that it forces you to think clearly about the code you are writing. What exactly is this method supposed to accomplish? What exactly does this array represent?

While additional documents and diagrams are in order for larger programs, the primary way to document code is to include *comments*, that is, sections of code what are visible to human readers but ignored by the compiler. Java offers three different syntaxes for comments, describe below.

### C-style comments

As in C, any code that begins with `/*` and ends with `*/` is a comment, even if it spans multiple lines.

```java
int a = 1;
/* These lines
are a comment */
int b = a + 1;
```

The other two syntaxes are preferable.

### Javadoc comments

A Javadoc comment is a special kind of C-style comment that begins with `/**`. This is best used right before a class, method, instance variable, etc.:

```java
/**
 * Returns the larger of a and b.
 */
static int max(int a, int b) {
    if (a > b) {
        return a;
    }
    return b;
}
```

When Java code is commented in this way, a program called Javadoc can be run (from the command line or through an IDE) to produce nicely-formatted HTML documents describing the code. These documents form an *application programming interface* (*API*), which is extremely useful for anyone who wants to use the classes you've defined without reading the code. An example is [the API for Java's Math class](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Math.html).

Another advantage of Javadoc comments is that many IDEs will read them to produce a pop-up tooltip wherever a method is called. This tooltip includes the method signature and the text from any associated Javadoc comment.

### C++-style comments

As in C++, `//` and anything after it on the same line is a comment. This is the preferable way to comment something within a method or to add a small comment at the end of a line.

```java
int height; // In centimeters
```

C++-style comments are also useful for commenting out a section of code, which is often useful while debugging.  Most IDEs will provide a hotkey to toggle C++-style comments at the beginning of every line in the selected section of code. In [IntelliJ IDEA](../development_tools/intellij_idea.md), this is `command-/` (Mac) / `ctrl-/` (Windows).

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 1.1 (print only)
- Horstmann, *Core Java, Volume 1, 11th Edition*, Section 3.2.
- [Google Java Style Guide](https://google.github.io/styleguide/javaguide.html)
- [How to Write Doc Comments for the Javadoc Tool](https://www.oracle.com/technetwork/java/javase/documentation/index-137868.html)
- Vermeulen *et al.*, *The Elements of Java Style*, Chapter 4 

## Questions
1. :star: How can you identify a Javadoc comment?
1. :star::star: How many comments do you need in your code?
1. :star::star: Which style is best for commenting out code?
1. :star::star: Why don't you include comments when writing code on the whiteboard?
## Answers
1. It starts with `/**` and ends with `*/`.
1. Include a Javadoc `/** */` comment before each method or class. Any method is particularly long or confusing, include C++-style `\\` comments within the method (or, better yet, consider breaking the method up into multiple methods). You don't have to provide Javadoc comments for methods that are private, are [completely obvious](https://google.github.io/styleguide/javaguide.html#s7.3.1-javadoc-exception-self-explanatory) (like standard getters and setters), or override default methods (like `toString` or `equals`). 
1. C++-style `//` comments. C-style `/* */` comments are dangerous because they don't nest:
    ```java
    /*
        int x = 1;
        /*
            int y = 2;
        */
        int z = 3;
    */
    ```
    The compiler sees this as one comment stretching from the *first* `/*` to the *first* `*/`, so the statement `int z = 3;` is not commented out and the last `*/` doesn't make sense.
1. The "documentation" for such code comes in the form of spoken words.
