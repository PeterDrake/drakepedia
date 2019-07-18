# Strings
## Overview

A String is a sequence of characters.

String literals are surrounded in double quotes:
```java
String s = "This is a String.";
```

Strings can be concatenated using the `+` operator, so the expression `"hot" + "dog"` has the value `"hotdog"`.

To determine if two Strings `a` and `b` are the same, use `a.equals(b)` instead of `a == b`.

In Java, unlike in C, a String is not exactly the same thing as an [array](arrays.md) of chars. The syntax for basic operations is slightly different:

Operation | Array of chars | String
--- | --- | ---
Declaration and initialization | `char[] a = {'a', 'b', 'c'};` | `String s = "abc";`
Length | `a.length`|`s.length()`
Element at index *i* | `a[i]` | `s.charAt(i)`

Another difference is that, unlike arrays, Strings are *immutable*: they cannot be changed. If `s` is the String `"hello"`, the expression `s.toUpperCase()` doesn't *modify* `s`, but the *value of the expression* is `"HELLO"`. If you wanted to change the value of `s`, you would need to say:
```java
s = s.toUpperCase();
```

Strings have many useful methods (things you can ask of them). In almost all cases, these return a new String. Several of the most useful are defined below.

Expression | Value | Notes
---|---|---
`"flower".contains("ow")`|`true`|`a` contains this substring
`"flower".indexOf('e')`|4|`'e'` first appears at this index
`"flower".substring(2, 5)`|`"owe"`|Includes characters from index 2 up to (but not including) index 5
`"Flower".toLowerCase()`|`"flower"`|Converts to lower case
`"flower".toUpperCase()`|`"FLOWER"`|Converts to upper case

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 1.2](https://introcs.cs.princeton.edu/java/12types/)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 3.6
- [Java API for the String class](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html)

## Questions
1. :star: Can a String be zero characters long?
1. :star::star: What is the value of `"three" + 3`?
1. :star::star: How would you get the last character of a String `s`?
1. :star::star: How would you get the last three characters of a String `s`?
1. :star::star::star: How would you convert a `char[]` `a` into a String?
1. :star::star::star: How would you convert a String `s` into a `char[]`?
1. :star::star::star: Can the [for each loop](../control_structures/loops.md#for_each_loops) be used to iterate through the characters of a String `s`?

## Answers
1. Yes: `""`
1. `"three3"`. When the `+` operator is given a String and a non-String value (in this case an int), the other value is converted into a String (in this case `"3"`) and then the two Strings are concatenated.
1. `s.charAt(s.length() - 1)`
1. `s.subString(s.length() - 3, s.length())`
1. `new String(a)`
1. `s.toCharArray()`
1. Not directly, but you can do it by converting the String to an array of chars:
    ```java
    for (char c : s.toCharArray()) {
        ...
    }
