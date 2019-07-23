# References
## Overview

Recall that a variable holds *exactly one thing*:

![x next to a box containing 5](x5.svg)

This is a simple story for [primitive types](primitive_types.md).

What if the type is an array type or a class? In this case, the box for the variable contains a *reference* to an object. We can think of this as an arrow pointing to the object. For example, if you
```java
int[] a = {6, 2, 5};
```
then you have:

![a next to a box containing an arrow, pointing to a row of three boxes. The three boxes contain the numbers 6, 2, and 5.](reference.svg)

The reference points to the entire object, not any particular part of it.
## Equality
## Null
## Garbage Collection
## Modifying Method Arguments
## Resources
## Questions
1. :star::star: Suppose we execute the following code (assuming Point is a class with a well-defined `equals` method):
    ```java
    Point a = new Point(1, 2);
    Point b = new Point(1, 2);
    Point c = b;
    ```
    1. Is `a == b`?
    1. Is `a.equals(b)`?
    1. Is `b == c`?
    1. Is `b.equals(c)`?
1. :star::star: Suppose we have defined
    ```java
    static void alter1(int[] a) {
        a[0] = 5;
    }
    ```
    and then we:
    ```java
    int[] b = {1, 2, 3, 4};
    alter1(b);
    ```
    What are the elements of `b` afterward?
1. :star::star: Suppose we have defined
    ```java
    static void alter2(int[] a) {
        a = new int[] {5, 6, 7, 8};
    }
    ```
    and then we:
    ```java
    int[] b = {1, 2, 3, 4};
    alter2(b);
    ```
    What are the elements of `b` afterward?
1. :star::star::star: What's the difference between a reference and a pointer?
## Answers
1.
    1. No (`a` and `b` refer to different objects)
    1. Yes
    1. Yes (`b` and `c` refer to the same object)
    1. Yes
1. 5, 2, 3, 4. Since `a` and `b` refer to the same array, alterations to the array on the other end of the reference are visible from either variable.
1. 1, 2, 3, 4. Making the local variable `a` point to a new array does not affect the external variable `b`.
1. Some sources will use these two words interchangeably. Indeed, a pointer (which is the address of a location in memory) is one way for a compiler to implement a reference. Other sources will insist that it's only a pointer if you have access to the address and can perform arithmetic on it to, for example, find the next consecutive location in memory. This is what people mean when they say, "C has pointers but Java does not." The designers of Java felt that the few additional shortcuts you can take with "true" pointers aren't worth the subtle and frustrating bugs that can result from messing with addresses directly.
