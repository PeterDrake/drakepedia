# java.lang
## Overview
The built-in java.lang packages contains a number of classes that are used extremely frequently in Java programs. You are not required to import these classes; you can use them directly.

The [API](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/package-summary.html) lists everything, but the most commonly used are:
### [Object](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Object.html)
This is the "cosmic superclass" from which all other classes descend.
### [System](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/System.html)
This class contains the static field `out` (as in `System.out.println`) and the methods [`exit`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/System.html#exit(int)) (to force a program to stop) and [`nanoTime`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/System.html#nanoTime()) (for timing programs).
### [String](https://github.com/PeterDrake/drakepedia/blob/master/data_structures/strings.md)
### Wrapper Classes
Integer, Boolean, Character, etc.
### [Math](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Math.html)
This class contains many static methods such as [`exp`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Math.html#exp(double)), [`floor`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Math.html#floor(double)), [`sin`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Math.html#sin(double)), and [`max`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Math.html#max(double,double)).
## Resources
- [java.lang API](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/package-summary.html)
## Questions
1. :star: In what package does the Integer class live?
1. :star::star::star: In the `System` class, shouldn't the constant field `out` be called `OUT`?
## Answers
1. `java.lang`
1. It's a very subtle point, but `out` isn't *really* a constant. While it can't be made to refer to a different object, the object to which it refers (a [`PrintStream`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/PrintStream.html)) can be modified.
