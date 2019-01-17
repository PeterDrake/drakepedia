# Loops
## Overview
Loops tell the computer to repeat some section of code many times, stopping at the appropriate point.
### While and Do While Loops
A `while` loop has the form
```java
while (test) {
    // Statements
}
```
where `test` is a boolean expression.

Its flow is:
1. If `test` is `false`, stop.
1. Execute the statements in the body of the loop.
1. Go back to step 1.

Strictly speaking, this the only loop you need, but the other variations can make your code clearer and more concise.

If you know that you want to execute the statements at least once, it is sometimes clearer to use a `do` `while` loop:
```java
do {
    // Statements
} while (test)
```
The flow of this version is:
1. Execute the statements in the body of the loop.
1. If `test` is `false`, stop.
1. Go back to step 1.
### Break and Continue
A `break` statement (just the word `break` followed by a semicolon) exits the current loop. If inside multiple nested loops, `break` only exits the innermost loop. This can be interpreted as "exit the loop".

A `continue` statement skips to the end of the body of the loop. This can be interpreted as "go on to the next pass through the loop".
### For Loops
A `for` loop has the form
```java
for (initialization; test; update) {
    // Statements
}
```
where `initialization` is a statement, `test` is a boolean expression, and `update` is another statement (without its usual closing semicolon).

Its flow is:
1. Execute `initialization`.
2. If `test` is false, stop.
3. Execute the statements in the body of the loop.
4. Execute `update`.

Here is a more concrete example:
```java
for (int i = 10; i >= 1; i--) {
    System.out.println(i);
}
```
Here:
- the initialization part declares a local variable `i` and sets it to 10,
- the test part verifies that `i` is at least 1, and
- the update part decrements `i`.

This loop therefore prints each of the integers from 10 down through 1.
### For Each Loops
A for each loop, also known as an enhanced `for` loop, has the form:
```java
for (type variable : structure) {
    // Statements
}
```
where `type` is a data type (such as `int` or `String`), `variable` is a new variable name, and `structure` is an array (or Iterable object) whose elements are of the specified type.

Its flow is:
1. If there are no elements in `structure` that haven't been visited yet, stop.
2. Assign `variable` to the next element in `structure`.
3. Execute the statements in the body of the loop.
4. Go back to step 1.

This loop is extremely handy for iterating through the elements of an array:
```java
for (int n : numbers) {
    System.out.println(n);
}
```
## Additional Resources
### Online
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 1.3](https://introcs.cs.princeton.edu/java/13flow/)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 1.3
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Sections 3.8.3, 3.8.4, 3.8.6, and 3.10.3
## Questions
1. :star: Explain how an `if` loop works.
## Answers
1. There is no such thing as an `if` loop. Loops potentially execute their bodies multiple times, but `if` statements do so at most once.
