# Wrapper Classes
## Overview
For every primitive type, there is a corresponding wrapper class in the java.util package. These are listed below.

| Primitive Type | Wrapper Class|
| --- | --- |
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Character |
| boolean | Boolean|

These classes define various static methods and constants associated with the class. For example, in the Integer class:

* `Integer.parseInt("23")` returns the int 23.
* `Integer.toBinaryString(23)` returns `"10111"`, which is the binary representation of the number 23.
* `Integer.MAX_VALUE` is the maximum value of an int, which is 2147483647 (which is 2<sup>31</sup> - 1).

## Converting Between Primitives and Wrapped Objects

There are some occasions where you will want to create an instance of a wrapper class, which is an object containing a primitive value. For example, perhaps you want a variable to be either an integer or `null`; an `Integer` would do the job.

You can convert between the two types manually. 

* `Integer.valueOf(23)` returns an Integer object containing the int 23.
* If `i` is an Integer object, then `i.intValue()` is the primitive int stored inside `i`.

This is a bit of a pain, so in almost all cases Java will do it for you; this is called *autoboxing*. For example,

```java
Integer i = 42;
```

automatically converts the primitive int `42` into an Integer object. After that,

```java
int n = i;
```

automatically converts `i` back into a primitive int.

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 3.3](https://introcs.cs.princeton.edu/java/33design/)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 5.4

## Questions
1. :star: What is the name of the wrapper class for the primitive type `int`?
1. :star: What is the wrapper class for the `String` type?
1. :star::star: What expression is true if two Longs `a` and `b` contain the same value?
## Answers
1. `Integer`
1. There is none. `String` is already an object type, not a primitive type.
1. `a.equals(b)`. As with other object types like `String`, the value of `a == b` is unpredictable.
