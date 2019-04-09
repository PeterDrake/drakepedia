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
    Is `a == b`? Is `a.equals(b)`? Is `b == c`? Is `b.equals(c)`?
## Answers
1. `a == b` is false, but the others are all true. `a` and `b` refer to different objects, but `b` and `c` refer to the same one.
