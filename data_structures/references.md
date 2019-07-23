# References
## Overview

Recall that a variable holds *exactly one thing*:

![x next to a box containing 5](x5.svg)

This is a simple story for [primitive types](primitive_types.md).

What if the type is an array type or a class? In this case, the box for the variable contains a *reference* to an object. You can think of a reference as an arrow pointing to the object. For example, if you
```java
int[] a = {6, 2, 5};
```
then you have:

![a next to a box containing an arrow, pointing to a row of three boxes. The three boxes contain the numbers 6, 2, and 5.](reference.svg)

The reference points to the entire object, not any particular part of it.
## Assignment and Aliases
The `=` assignment operator copies the contents of one box into another. For primitive types, this is easy to understand. If
you
```java
int x = 4;
int y = x;
```
then the value 4 is copied from `x`'s box into `y`'s:

![The box for x contains 4. The box for y also contains 4.](simple_assignment.svg)

With reference, an assignment still copies the contents of the box, but now that means copying the *reference*, not the object on the other end. For example, if you
```java
int[] a = {1, 2, 3};
int[] b = a;
```
then you get two references to the same array:

![The box for a and the box for b each contain the tail of an arrow. Both arrows point at the array containing 1, 2, and 3.](alias.svg)

`a` and `b` are said to be *aliases* because they refer to the same array. A consequence of this is that, if you modify the array to which `a` refers, you are also modify the array to which `b` refers (because they're the same one).

### Methods Modifying Their Arguments
Methods cannot modify their arguments, but references provide a loophole.

If a method has a primitive parameter, like
```java
static void f(int x) {
    x = 100;
}
```
then doing something like
```java
int y = 7;
f(y);
```
has no effect on `y`. The parameter `x` gets a *copy* of the value stored in `y`, so no matter what happens to `x`, `y` is unchanged.

If, on the other hand, a method has a parameter of an object type, like:
```java
static void g(int[] a) {
    a[0] = 3;
}
```
and then you
```java
int[] b = new int[5];
g(b);
```
then the array to which `b` refers *has* been modified, because the parameter `a` is an alias for the argument `b`.

## Equality
References make the notion of equality more complex.

The `==` operator asks whether two boxes contain the same thing: the same primitive value or references to the same object. For example, suppose you have defined a `Point` class
```java
class Point {
    int x;
    int y;
}
```
and then:
```java
Point p = new Point();
p.x = 3;
p.y = 4;
Point q = p;
Point r = new Point();
r.x = 3;
r.y = 4;
```

Memory now looks like this:

![p contains a reference to a Point object in which x is 3 and y is 4. q contains another reference to the same Point. r contains a reference to a second point in which x is 3 and y is 4.](equality.svg)

then `p == q` but `p != r` because `p` and `r` do not refer to *the same object*.

We are often interested in whether two objects have the same *contents*. In this sense, `p` and `r` are equal. For many built-in classes (including String), the expression `p.equals(q)` is true if `p` and `q` have the same contents. This is the preferred way to compare objects.

You can also write `equals` methods for your own classes.
## Null
The keyword `null` is a reference to nothing. If you
```java
String s = null;
```
Then `s` doesn't refer to anything. I draw this as a line connected to a dot rather than to an arrowhead:

![s contains a reference to nothing](null.svg)

Trying to do anything with `s`, such as asking for `s.length()`, results in a `NullPointerException` because there is no String object on the other end.

`null` is the default value for object types.

## Garbage Collection
## Resources
## Questions
NULL WORKS WITH ==
COMPARING ARRAYS
1. :star: What is the term for two references to the same object?
1. :star: Which types use references?
1. :star::star: Suppose you execute the following code (assuming Point is a class with a well-defined `equals` method):
    ```java
    Point a = new Point(1, 2);
    Point b = new Point(1, 2);
    Point c = b;
    ```
    1. Is `a == b`?
    1. Is `a.equals(b)`?
    1. Is `b == c`?
    1. Is `b.equals(c)`?
1. :star::star: If you
    ```java
    int[] a = {1, 2, 3};
    int[] b = a;
    a[1] = 5;
    ```
    then what is the value of `b[1]`?
1. :star::star: Suppose you have defined
    ```java
    static void alter1(int[] a) {
        a[0] = 5;
    }
    ```
    and then you:
    ```java
    int[] b = {1, 2, 3, 4};
    alter1(b);
    ```
    What are the elements of `b` afterward?
1. :star::star: Suppose you have defined
    ```java
    static void alter2(int[] a) {
        a = new int[] {5, 6, 7, 8};
    }
    ```
    and then you:
    ```java
    int[] b = {1, 2, 3, 4};
    alter2(b);
    ```
    What are the elements of `b` afterward?
1. :star::star::star: What's the difference between a reference and a pointer?
## Answers
1. Aliases.
1. All non-primitive types, that is, array types and types defined by classes and interfaces.
1.
    1. No (`a` and `b` refer to different objects)
    1. Yes
    1. Yes (`b` and `c` refer to the same object)
    1. Yes
1. 5, because `a` and `b` are aliases. There is only one array, which can be accessed via either reference.
1. 5, 2, 3, 4. Since `a` and `b` refer to the same array, alterations to the array on the other end of the reference are visible from either variable.
1. 1, 2, 3, 4. Making the local variable `a` point to a new array does not affect the external variable `b`.
1. Some sources will use these two words interchangeably. Indeed, a pointer (which is the address of a location in memory) is one way for a compiler to implement a reference. Other sources will insist that it's only a pointer if you have access to the address and can perform arithmetic on it to, for example, find the next consecutive location in memory. This is what people mean when they say, "C has pointers but Java does not." The designers of Java felt that the few additional shortcuts you can take with "true" pointers aren't worth the subtle and frustrating bugs that can result from messing with addresses directly.
