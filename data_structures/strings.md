# Strings
## Overview

A String is a sequence of characters.

String literals are surrounded in double quotes:
```java
String s = "This is a String.";
```

Strings can be concatenated using the `+` operator, so the expression `"hot" + "dog"` has the value `"hotdog"`.

In Java, unlike in C, a String is not exactly the same thing as an [array](arrays.md) of chars. The syntax for basic operations is slightly different:

| Operation | Array of chars | String |
| - | - |
| Declaration and initialization | `char[] a = {'a', 'b', 'c'};` | `String s = "abc";` |
| Length | `a.length`|`s.length()` |
| Element at index *i* | `a[i]` | `s.charAt(i)` |


immutable

methods

## Resources

## Questions
1. :star: What is the value of `"three" + 3`?
foreach

## Answers
1. `"three3"`. When the `+` operator is given a String and a non-String value (in this case an int), the other value is converted into a String (in this case `"3"`) and then the two Strings are concatenated.
