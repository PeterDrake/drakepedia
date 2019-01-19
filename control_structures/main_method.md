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
### Expressions and Statements
An *expression* has a value: `2 + 2`. Expressions can be made up of other expressions: `5 + (8 - 4)`.

A *statement* does something: `System.out.println("Hello, world!");`. Statements often contain expressions, such as `"Hello, world!"` within the previous statement. Complex statements, such as [loops](loops.md), can contain other statements.

Some things, such as assignment statements and [method calls](functional_decomposition.md#calling-methods), are *both* expressions and statements, because they have values *and* do things.

## Additional Resources
### Online
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 1.1](https://introcs.cs.princeton.edu/java/11hello/)
- Oracle's *Essentials of the Java Programming Language*, [Lesson 1](https://www.oracle.com/technetwork/java/compile-136656.html)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 1.1
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 3.1
## Questions
1. Is `x > 0` a statement or an expression?
1. :star::star: What, if anything, can be changed on the first line of the program?
1. :star::star: What, if anything, can be changed in the line:
```java
public static void main(String[] args) {
```
## Answers
1. It is an expression. Its value is either `true` or `false`.
1. The keyword `public` is optional. It doesn't matter unless your code is divided into multiple packages. The name of the program (`Hello` in the example above) can also change, but must match the name of the file (in this case `Hello.java`).
1. The argument name `args` can be changed to anything. Everything else must be exactly the same.
