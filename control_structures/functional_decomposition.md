# Functional Decomposition
## Overview
A long program can be greatly improved by breaking it down into multiple *functions*, represented in Java as static methods. This has many advantages:
- Redundant code (repeating the same statements in several places) is avoided, making the code shorter.
- The structure of the code is made clearer, making the code easier to read and write.
- Individual methods can be tested, making the code easier to debug.
- Methods can often be reused to solve other problems.
### Calling Methods
To call a method defined in the same class, use this syntax:
```java
foo(a, b + 1);
```
Here `foo` is the name of the method and `a` and `b + 1` are arguments, expressions whose values are given to the method. If the method has a return type other than `void`, the method call is also an expression, so you can (e.g.) store the resulting value in a variable:
```java
int c = foo(a, b + 1);
```
To call a method defined in another class, use this syntax:
```java
StdDraw.rectangle(0.3, 0.8, 0.1, 0.1);
```
Here `StdDraw` is the name of the class where the `rectangle` method is defined.
### Defining Methods
You may define any number of methods within a class, using this syntax:
```java
static type name(type1 argument1, type2 argument2, ...) {
    // Statements
}
```
where:

- `type` is the type of the value returned by the method (or `void` if the method doesn't return a value),
- `name` is the name of the method,
- `type1`, `type2`, and so on are the types of the arguments, and
- `argument1`, `argument2`, and so on are the names of the arguments.

Here is a more concrete example:
```java
static int square(int n) {
    return n * n;
}
```

## Additional Resources
### Online
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 2.1](https://introcs.cs.princeton.edu/java/13function/)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 2.1
## Questions
1. :star: How do you call a method that doesn't take any arguments?
1. :star::star: What's wrong with the following method call?
    ```java
    double s = Math.sin(double x);
    ```
## Answers
1. Don't put anything between the parentheses:
    ```java
    quux();
    ```
1. Argument types aren't specified. This should be:
    ```java
    double s = Math.sin(x);
    ```
