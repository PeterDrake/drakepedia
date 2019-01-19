# Primitive Types
The table below shows Java's eight primitive types. You will rarely use any but the four in bold.

Integers | Floating Point Numbers | Characters | Booleans
-|-|-|-
byte<br>short<br>**int**<br>long | float<br>**double** | **char** | **boolean**

The numeric types vary in how many bits they allocate for storage; larger types can hold larger numbers but use more memory.

These types are called *primitive* because they aren't made of smaller things. The built-in type String, in contrast, is not primitive because a String is made of characters.
## Literals
A *literal* is a value that is used exactly as it appears in the program.

Type | Examples of Literals
-|-
int | `23` `-100`
double | `3.14159` `1.3e-10`
char | `'a'` `'\n'`
boolean | `true` `false`

There are two cases where literals are of non-primitive types:
- String literals are in quotations marks: `"Hello"`.
- The literal `null` represents a null reference.
## Type Conversion
When a certain type of expected, that type must be used. There are two exceptions:
- When Java can do the conversion without losing any information, it will do so. For example, an int can be converted to a double. Thus, when adding `1 + 1.5`, the `+` operator needs its two operands to be of the same type, so Java automatically converts the int `1` into the double `1.0`.
- You can explicitly *cast* one type to another. The expression `(int) 3.9` converts the double `3.9` into the int `3`, truncating the non-integer part.
## Overview
## Additional Resources
### Online
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 1.1](https://introcs.cs.princeton.edu/java/12types/)
- Wired, [No, 'Gangnam Style' Didn't Break YouTube. We Did the Math](https://www.wired.com/2014/12/gangnam-style-youtube-math/)
- Kotaku, [Why Gandhi Is Such an Asshole in *Civilization*](https://kotaku.com/why-gandhi-is-such-an-asshole-in-civilization-1653818245)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 1.2
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 3.3
## Questions
## Answers
