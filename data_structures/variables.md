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

## Resources

## Questions
1. :star: If `alive` is a boolean variable, how can `alive == true` be replaced with a shorter expression?

## Answers
1. If `alive == true`, `alive` is true; if not, `alive` is false. In other words, `alive` and `alive == true` always have exactly the same value. The shorter version is always preferable as it is clearer, is more concise, and avoids the risk of accidentally typing `alive = true` (which is an assignment, not a comparison).
