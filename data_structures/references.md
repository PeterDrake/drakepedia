# References
## Overview
## Equality
## Null
## Additional Resources
## Questions
1. :star: Suppose we execute the following code (assuming Point is a class with a well-defined `equals` method):
    ```java
    Point a = new Point(1, 2);
    Point b = new Point(1, 2);
    Point c = b;
    ```
    1. Is `a == b`?
    1. Is `a.equals(b)`?
    1. Is `b == c`?
    1. Is `b.equals(c)`?
## Answers
1.
    1. No (`a` and `b` refer to different objects)
    1. Yes
    1. Yes (`b` and `c` refer to the same object)
    1. Yes
