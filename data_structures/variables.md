# Variables

## Overview

In computer science, a *variable* is a named location to store a value. (Mathematicians and statisticians use the word in slightly different ways.)

A variable must first be *declared*:
```java
int x;
```
In this statement, `int` is the variable's *type* and `x` is its name.

It is useful to think of a variable as a box to hold something:

![x next to an empty box](x.svg)

Before the variable can be used, it must be *initialized*, that is, assigned an initial value:
```java
x = 5;
```
Now there's something in the box:

![x next to a box containing 5](x5.svg)

Once the variable is initialized, the box always contains *exactly one value*. It can't be empty and it can't contain more than one value. (Arrays, Strings, and other non-primitive objects get around this limitation by putting a [reference](references.md) in the box.) The value must be of the specified type.

It is common to declare and initialize a variable on the same line:
```java
int x = 5;
```

The variable, as an expression, now stands for its stored value, so we can do things like:
```java
System.out.println(x);
```

The variable can be given a different value, replacing what was in the box, with an assignment statement:
```java
x = -17;
```

### Scope

The *scope* of a variable is the region of code where the variable can be accessed. This extends from the point where the variable is declared until the next closing curly brace at the end of an [if / else statement](../control_structures/if_else.md), [loop](../control_structures/loops.md), or [method](../control_structures/functional_decomposition.md). The scope of a method parameter is the entire method.

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 1.2](https://introcs.cs.princeton.edu/java/12types/)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 3.4

## Questions
1. :star: Explain the difference between `x = y;` and `x == y`.
1. :star: Is the following code legal?
    ```java
    int x = 2;
    x = 3;
    ```
1. :star: Is the following code legal?
    ```java
    int x = 2;
    int x = 3;
    ```
1. :star: Is the following code legal?
    ```java
    int variable = 2;
    int VARIABLE = 3;
    ```
1. :star: What is the scope of variable `n` in the following code snippet?
   ```java
   int fac(int n) {
       int p = 1;
       for (int i = 1; i <= n; i++)
           p = p * i;
       return p;
   }
   ```
1. :star: What is the scope of variable `i` in the following code snippet?
   ```java
   int fac(int n) {
       int p = 1;
       for (int i = 1; i <= n; i++)
           p = p * i;
       return p;
   }
   ```
1. :star::star: If `alive` is a boolean variable, how can `alive == true` be replaced with a shorter expression?
1. :star::star: Do `x = y;` and `y = x;` mean the same thing?
1. :star::star: Is `3 = x;` a legal statement?
1. :star::star: How would you swap the values of two variables `x` and `y`?
1. :star::star::star: How would you swap the values of two variables `x` and `y` *without using a third variable*?
1. :star::star::star: Is `a = b = c;` a legal statement?
## Answers
1. `x = y;` is a statement that causes `x` to contain a copy of the value of `y`. `x == y` is a boolean expression that is true if and only if `x` and `y` contain the same value.
1. Yes. It doesn't make sense as algebra, where the `=` symbol is used to *state* that two expressions are equal, but it's fine in Java. It creates a variable `x`, assigns it the value 2, and then replaces that value with 3.
1. No. Once a variable has been declared, you cannot declare a second variable with the same name in the same scope.
1. Yes. Since Java is case-sensitive, `variable` and `VARIABLE` are different variables.
1. The scope of `n` is the entire method `fac()`.
1. The scope of `i` is the `for` loop.
1. If `alive == true`, `alive` is true; if not, `alive` is false. In other words, `alive` and `alive == true` always have exactly the same value. The shorter version is always preferable as it is clearer, is more concise, and avoids the risk of accidentally typing `alive = true` (which is an assignment, not a comparison).
1. No. If `x` was 1 and `y` was 2, then `x = y;` would change `x`'s value to 2, but `y = x;` would change `y`'s value to 1.
1. No. The value on the left side of an assignment statement must be a variable (or some other place where a value can be stored, like an array element).
1.
    ```java
    int temp = x;
    x = y;
    y = temp;
    ```
    To remember this, imagine that you have an object (say, a can of beans) in each hand. To swap them, you put one down on the table, move the other one to your newly-empty hand, and then pick up the one on the table. This analogy is slightly strained because `int temp = x;` doesn't empty out `x`, it just copies the value of `x` into `temp`.
1. Surprisingly, you can accomplish this (for integer types) using the bitwise xor operator:
    ```java
    x = x ^ y;
    y = x ^ y;
    x = x ^ y;
    ```
    For boolean variables, you could do the same thing with the logical xor operator `!=`.
1. Yes. This copies the value of `c` into `b`, and then copies that value into `a`. This works because `b = c` is also an expression, whose value is the value of `c`. Furthermore, multiple assignments are handled from right to left to allow for exactly this sort of thing. `a = b = c;` is therefore equivalent to `a = (b = c);`.
