# References
## Overview
## Equality
## Null
## Additional Resources
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
    void alter1(int[] a) {
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
    void alter2(int[] a) {
        a = new int[] {5, 6, 7, 8};
    }
    ```
    and then we:
    ```java
    int[] b = {1, 2, 3, 4};
    alter2(b);
    ```
    What are the elements of `b` afterward?
## Answers
1.
    1. No (`a` and `b` refer to different objects)
    1. Yes
    1. Yes (`b` and `c` refer to the same object)
    1. Yes
1. 5, 2, 3, 4. Since `a` and `b` refer to the same array, alterations to the array on the other end of the reference are visible from either variable.
1. 1, 2, 3, 4. Making the local variable `a` point to a new array does not affect the external variable `b`.
