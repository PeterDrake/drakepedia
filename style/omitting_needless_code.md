# Omitting Needless Code
## Overview
> Omit needless words.
>
> Vigorous writing is concise. A sentence should contain no unnecessary words, a paragraph no unnecessary sentences, for the same
> reason that a drawing should have no unnecessary lines and a machine no unnecessary parts. This requires not that the writer make
> all sentences short, or avoid all detail and treat subjects only in outline, but that every word tell.
>
> -Strunk and White, *The Elements of Style*

Programs should be clear. To that end, they should be concise. An overly long program is tedious to write and difficult to read and maintain. A program that solves a problem with a small amount of clear code is considered *elegant*.

Crafting elegant solutions is part of the art of programming. Several techniques will steer you in the right direction.

### Do not store values that will never be read

Consider this method to determine whether a number is even:

```java
static boolean isEven(int n) {
    boolean result = false;
    if (n % 2 == 0) {
        result = true;
    } else if (n % 2 == 1) {
        result = true;
    }
    return result;
}
```

The initial value of `result` will never be read, it is *always* going to be set in the `if` statement, so there's no need to initialize it:

```java
static boolean isEven(int n) {
    boolean result;
    if (n % 2 == 0) {
        result = true;
    } else if (n % 2 == 1) {
        result = true;
    }
    return result;
}
```

This version won't compile because the compiler doesn't *know* that `result` will always get a value. You can fix that with the next technique.

### Don't check for conditions that must be true

Continuing the example, `n % 2` must either be 0 or 1. You therefore don't need the second `if` check:

```java
static boolean isEven(int n) {
    boolean result;
    if (n % 2 == 0) {
        result = true;
    } else {
        result = true;
    }
    return result;
}
```

This is correct and shorter than the original, but you can do even better.

### Stop as soon as you know the answer

In this example, once the value of `result` has been set, it will never change. It's best to simply...

### Avoid redundant code

Suppose we want to determine if either of two Strings contains a space. We could do this:

```java
static boolean eitherContainsSpace(String a, String b) {
    if (a.contains(' ')) {
```


### Use shorter expressions

### Minimize special cases

### Separate control from data

## Resources
## Questions
1. :star::star: Is a shorter program always preferable?
TODO isEven method
1. :star::star: Using an array, refactor the method below to avoid the long if/else chain.
    ```java
    public String toString() {
        if (n == 0) {
            return "red";
        } else if (n == 1) {
            return "orange";
        } else if (n == 2) {
            return "yellow";
        } else if (n == 3) {
            return "green";
        } else if (n == 4) {
            return "blue";
        } else if (n == 5) {
            return "indigo";
        } else {
            return "violet";
        }
    }
    ```
## Answers
1. No. The goal is clarity, and to that end we omit only *needless* code. Programmers sometimes play ["code golf"](https://en.wikipedia.org/wiki/Code_golf), solving a problem in as few characters as possible, but a program so short that it becomes cryptic serves nothing but the ego of the programmer.
1.
    ```java
    public String toString() {
        String[] colors = {"red", "orange", "yellow", "green", "blue", "indigo", "violet"};
        return colors[n];
    }
    ```
    It would be even better to declare `COLORS` as a constant so that it doesn't have to be created each time `toString` is called.
