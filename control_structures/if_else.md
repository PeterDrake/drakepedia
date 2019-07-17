# If Statements
## Overview
An `if` statement has either the form
<pre>
if (<em>test</em>) {
    <em>statement</em>
    ...
}
</pre>
or the form
<pre>
if (<em>test</em>) {
    <em>statement</em>
    ...
} else {
    <em>statement</em>
    ...
}
</pre>
where *test* is a boolean expression. The first version executes the statements in the body if the value of *test* is `true`. The second executes the first batch of statements if *test* is `true` and the second batch if it is `false`.

Like other control structures involving curly braces, `if` statements can be nested inside each other.

Some sources call an `if` statement a *conditional statement* or *branch*.
## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 1.3](https://introcs.cs.princeton.edu/java/13flow/)
- Goeschel, [Reflections on Curly Braces](https://blog.codecentric.de/en/2014/02/curly-braces/)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 3.8.2
## Questions
1. :star::star: Explain the difference between
    ```java
    if (test1) {
        System.out.println("A");
    }
    if (test2) {
        System.out.println("B");
    }
    ```
    and
    ```java
    if (test1) {
        System.out.println("A");
        if (test2) {
            System.out.println("B");
        }
    }
    ```
1. :star::star: Explain the difference between
    ```java
    if (test1) {
        System.out.println("A");
    }
    if (test2) {
        System.out.println("B");
    }
    ```
    and
    ```java
    if (test1) {
        System.out.println("A");
    } else if (test2) {
        System.out.println("B");
    }
    ```
1. :star::star: What is printed by the statement below?
    ```java
    if (false)
        System.out.println("A");
        System.out.println("B");
    ```
1. :star::star: How can the following statement be shortened?
    ```java
    if (test) {
        System.out.println("A");
    } else if (!test) {
        System.out.println("B");
    }
    ```
1. :star::star: The first form at the top of this page is called a *one-armed* if statement. The second form is a *two-armed* if statement. How could you use if statements to make a three-way decision? 
## Answers
1. The second version only prints `B` if *both* `test1` and `test2` are true.
1. The second version only prints `B` if `test1` is `false` *and* `test2` is `true`.
1. `B`. The indentation is deceptive; only the first `println` statement is part of the `if` statement. To avoid accidentally creating confusing code like this, *always* use the curly braces.
1.
    ```java
    if (test) {
        System.out.println("A");
    } else {
        System.out.println("B");
    }
    ```
    If `test` was `false`, then `!test` *must* be `true`; there's no need to waste code or computation checking it.
1. asdfdsaf
