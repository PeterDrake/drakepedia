# Functional Decomposition
## Overview
A long program can be greatly improved by breaking it down into multiple *functions*, represented in Java as static methods. This has many advantages:
- Redundant code (repeating the same statements in several places) is avoided, making the code shorter.
- The structure of the code is made clearer, making the code easier to read and write.
- Individual methods can be tested, making the code easier to debug.
- Methods can often be reused to solve other problems.

A well-designed method should *do only one thing*: either return a value or have some side effect (modify a data structure in memory, draw something on the screen, etc.). 
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
### Return Statements
To return a value from a method, use this syntax:
```java
return expr;
```
where `expr` is an expression of the appropriate type. If the method's return type is `void`, simply:
```java
return;
```
Once a `return` statement is executed, the method exits. No other code in the method is run after that. If there is code that cannot be reached because it is after a `return` statement, the method will not compile.

A method with a return type of `void` doesn't need a `return` statement; it automatically returns at the end of the method.

If the return type is not `void`, the method *must* return a value of that type. This must be true in every path through the method (taking different branches in `if`/`else` statements, entering or not entering loops, etc.). If there is a path through the method that does not lead to a return statement, the method will not compile.
### The Call Stack
When your `main` method calls a method, your program pauses, runs the other method, and then picks up where it left off in `main`. Behind the scenes, a structure called a *call frame* keeps track of where you are in each method as well as any local variables.

If `main` call a method that in turn calls another method, you now have a *call stack*, with one call frame for the currently running method and one for each of the paused methods. Every time you call a method, a new call frame is pushed onto the top of the stack. Every time a method returns, a call frame is popped off the top of the stack and the next method down resumes. When the bottom call frame (for `main`) is popped off, the program ends.
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
1. :star::star: Why does the method below not compile?
    ```java
    static int foo() {
        for (int i = 0; i < 10; i++) {
            if (i == 5) {
                return 1;
            }
        }
    }
    ```
1. :star::star::star: Is it legal to have more than one method with the same name in the same class?
## Answers
1. Don't put anything between the parentheses:
    ```java
    quux();
    ```
1. Argument types aren't specified. This should be:
    ```java
    double s = Math.sin(x);
    ```
1. The compiler can't predict that the `return` statement will always be reached. (It may be obvious to you that it will for this particular program, but in general it is impossible for the compiler to predict what a program will do.)
1. Yes, as long as their argument lists differ in number or type. This is called *overloading*. When you call the method, Java uses the types of the arguments you provide to determine which version to use.
