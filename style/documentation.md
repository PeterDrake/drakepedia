# Documentation
## Overview
> Documentation is a love letter that you write to your future self.
>
> -Damian Conway, *Perl Best Practices*

Code is not just for the computer. It's also read by other people who need to understand how it works, debug it, or add new features. Unless it is thoroughly documented, even your own code will be completely mysterious to you if you haven't looked at it in a few months.

> Writing is thinking. To write well is to think clearly. That's why it's so hard.
>
> David McCullough, interview with NEH chairman Bruce Cole, *Humanities 23:4*

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

A Javadoc comment is a special kind of C-style comment that begins with `/**`. This is best used rigth before a class, method, instance variable, etc.

When Java code is commented in this way, a program called Javadoc can be run (from the command line or through an IDE) to produce nicely-formatted HTML documents describing the code. These documents form an *application programming interface* (*API*), which is extremely useful for anyone who wants to use the classes you've defined without reading the code. An example is [the API for Java's Math class](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Math.html).

Another advantage of Javadoc comments is that many IDEs will read them to produce a pop-up tooltip wherever a method is called. This tooltip includes the method signature and the text from any associated Javadoc comment.

### C++-style comments

As in C++, 
## Resources
## Questions
no comments in class?
which style is best for commenting out code
1. :star: How can you identify a Javadoc comment?
## Answers
1. It starts with `/**` and ends with `*/`.
