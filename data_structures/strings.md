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

Strings have [many useful methods](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html) (things you can ask of them). In almost all cases, these return a new String. Several of the most useful are defined below.

Expression | Value | Notes
---|---|---
`"flower".contains("ow")`|`true`|`a` contains this substring
`"flower".indexOf('e')`|4|`'e'` first appears at this position
`"flower".substring(2, 5)`|`"owe"`|Includes characters from index 2 up to (but not including) index 5
`"Flower".toLowerCase()`|`"flower"`|Converts to lower case
`"flower".toUpperCase()`|`"FLOWER"`|Converts to upper case

## Resources

## Questions
1. :star: What is the value of `"three" + 3`?
foreach

## Answers
1. `"three3"`. When the `+` operator is given a String and a non-String value (in this case an int), the other value is converted into a String (in this case `"3"`) and then the two Strings are concatenated.
