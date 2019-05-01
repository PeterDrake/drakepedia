# Loops
## Overview
Loops tell the computer to repeat some section of code many times, stopping at the appropriate point.
### While and Do While Loops
A `while` loop has the form
<pre>
while (<em>test</em>) {
    <em>statement</em>
    ...
}
</pre>
where *test* is a boolean expression.

Its flow is:
1. If *test* is `false`, stop.
1. Execute the statements in the body of the loop.
1. Go back to step 1.

Strictly speaking, this is the only loop you need, but the other variations can make your code clearer and more concise.

If you know that you want to execute the statements at least once, it is sometimes clearer to use a `do` `while` loop:
<pre>
do {
    <em>statement</em>
    ...
} while (<em>test</em>)
</pre>
The flow of this version is:
1. Execute the statements in the body of the loop.
1. If *test* is `false`, stop.
1. Go back to step 1.
### Break and Continue
A `break` statement (just the word `break` followed by a semicolon) exits the current loop. If inside multiple nested loops, `break` only exits the innermost loop. This can be interpreted as "exit the loop".

A `continue` statement skips to the end of the body of the loop. This can be interpreted as "go on to the next pass through the loop".
### For Loops
A `for` loop has the form
<pre>
for (<em>initialization</em>; <em>test</em>; <em>update</em>) {
    <em>statement</em>
    ...
}
</pre>
where *initialization* is a statement, *test* is a boolean expression, and *update* is another statement (without its usual closing semicolon).

Its flow is:
1. Execute *initialization*.
2. If *test* is false, stop.
3. Execute the statements in the body of the loop.
4. Execute *update*.

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
<pre>
for (<em>type</em> <em>variable</em> : <em>structure</em>) {
    <em>statement</em>
    ...
}
</pre>
where *type* is a data type (such as `int` or `String`), *variable* is a new variable name, and *structure* is an array (or Iterable object) whose elements are of the specified type.

Its flow is:
1. If there are no elements in *structure* that haven't been visited yet, stop.
2. Assign *variable* to the next element in *structure*.
3. Execute the statements in the body of the loop.
4. Go back to step 1.

The for each loop is extremely handy for iterating through the elements of an array:
```java
for (int n : numbers) {
    System.out.println(n);
}
```
The first line can be read, "for each `int` `n` in `numbers`...".
## Additional Resources
### Online
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 1.3](https://introcs.cs.princeton.edu/java/13flow/)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 1.3
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Sections 3.8.3, 3.8.4, 3.8.6, and 3.10.3
## Questions
1. :star: What is printed by the following code?
    ```java
    for (int i = 0; i < 5; i++) {
        System.out.print(i);
    }
    ```    
1. :star: Explain how an `if` loop works.
1. :star: How would you write the `for` loop below as a `while` loop?
    ```java
    for (int i = 0; i < 5; i++) {
        System.out.println(i);
    }
    ```
1. :star: How would you write the `for` loop below as a for each loop? Assume `a` is an array of Strings.
    ```java
    for (int i = 0; i < a.length; i++) {
        System.out.println(a[i]);
    }
    ```
1. :star::star: What's the best loop to use to iterate through the elements of an array *backward*?
1. :star::star: What's the best loop to use to modify an array of doubles to make each element 10 times as large?
1. :star::star: Can a loop body be empty?
1. :star::star: Which parts, if any, of the first line of a `for` loop can be omitted?
1. :star::star: A variable declared in the initialization part of a `for` loop is only visible inside that loop. What can we do if we need to access it after the loop ends (to see its final value)?
1. :star::star: What does the code below accomplish? Assume `a` is an array of ints.
    ```java
    for (int i = 0; i < a.length / 2; i++) {
        int j = a.length - 1 - i;
        int temp = a[i];
        a[i] = a[j];
        a[j] = temp;
    }
    ```
## Answers
1. `01234`
1. There is no such thing as an `if` loop. Loops potentially execute their bodies multiple times, but `if` statements do so at most once.
1.
    ```java
    int i = 0;
    while (i < 5) {
        System.out.println(i);
        i++;
    }
    ```
    This isn't *exactly* equivalent, because the local variable `i` is still visible after the loop in this version. In the
    `for` loop, `i` is only visible inside the loop.
1.
    ```java
    for (String s : a) {
        System.out.println(s);
    }
    ```
1. A `for` loop like:
    ```java
    for (int i = array.length - 1; i >= 0; i--) {
        ...
    }
    ```
    This could also be done with a `while` loop, but it would be more code. A for each loop wouldn't work because it only goes through a structure forward.
1. A `for` loop:
    ```java
    for (int i = 0; i < array.length; i++) {
        array[i] = array[i] * 10; // If you know about *=, that would be even better
    }
    ```
    This could also be done with a `while` loop, but it would be more code. A for each loop wouldn't work because it doesn't give you access to the *indices* into the array, just the elements themselves.
1. Sure. This is sometimes useful when all of the necessary work is done in the first line of the loop.
1. All three of them. Empty initialization and update parts do nothing; an empty test always counts as `true`. Thus,
    ```java
    for ( ; ; ) {
        ...
    }
    ```
    is equivalent to:
    ```java
    while (true) {
        ...
    }
    ```
    In this extreme case, the `while` loop is clearer.
1. Declare the variable before the loop starts:
    ```java
    int i;
    for (i = 0; i < 10; i++) {
        ...
    }
    // Now i is still visible here
    ```
1. It reverses the order of the elements of `a`.
