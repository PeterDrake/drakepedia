# Main Method
## Overview
A simple Java program is structured like this:
```java
public class Hello {

    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }

}
```
Any number of statements can replace the line
```java
System.out.println("Hello, world!");
```

The statement below will exit the `main` method (and therefore the program).
```java
return;
```
## Additional Resources
### Online
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 1.1](https://introcs.cs.princeton.edu/java/11hello/)
- Oracle's *Essentials of the Java Programming Language*, [Lesson 1](https://www.oracle.com/technetwork/java/compile-136656.html)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 1.1
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Sections 2.1-2.2
## Questions
1. :star::star: What, if anything, can be changed on the first line of the program?
1. :star::star: What, if anything, can be changed in the line:
```java
public static void main(String[] args) {
```
## Answers
1. The keyword `public` is optional. It doesn't matter unless your code is divided into multiple packages. The name of the program (`Hello` in the example above) can also change, but must match the name of the file (in this case `Hello.java`).
1. The argument name `args` can be changed to anything. Everything else must be exactly the same.
