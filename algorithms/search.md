# Search
This section deals with the question of whether some key (value) is present in an array.
## Linear Search
The obvious approach, *linear search*, is to simply look at each element of the array using a loop:

```java
/** Returns the first index at which key appears in a, or -1 if it does not. */
public static int linearSearch(int key, int[] a) {
    for (int i = 0; i < a.length; i++) {
        if (a[i] == key) {
            return i;
        }
    }
    return -1;
}
```

In the worst case, when `key` is either the last element or not present, this takes linear time. On average, assuming `key` is present and equally likely to be in any postion, about half of the elements will have to be inspected, which is still linear.

## The Comparable Interface
It is possible to do better than linear search if the array is *sorted* in increasing order. This is only meaningful for arrays of types that can be compared to see if one value is larger than another. Clearly numbers can be compared. Strings can also be compared in *lexicographical order* (which is similar to alphabetical order, but accounts for with upper and lower case letters, digits, and other characters).

Rather than provide overloaded methods to account for every such type, you can use the built-in `Comparable` interface. Built-in classes like String and all of the wrapper classes implement Comparable. You could also implement it with your own classes.

Comparable has one method, `compareTo`. If `a` and `b` are instances of the same Comparable class, then `a.compareTo(b)` returns:
* a negative number if `a` is less than `b`,
* zero if `a` is equal to `b`, and
* a positive number if `a` is greater than `b`.

Don't try to read anything into the size of the returned number. Only the sign matters.

If you define your own Comparable class, be sure to define `equals` and `compareTo` consistently so that `a.equals(b)` returns true exactly when `a.compareTo(b)` returns zero.

## Binary Search

## Resources

* [Comparable](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Comparable.html) (Java API)

## Questions
1. :star: What is the order of the worst-case running time of binary search?
1. :star::star: What is the order of the best-case running time of linear search?
1. :star::star: Complete the method below.
    ```java
    /** Returns the first index at which key appears in a, or -1 if it does not. */
    public static int linearSearch(Object key, Object[] a) {
      
    }
    ```
1. :star::star::star: Wouldn't it be clearer for Comparable to define methods `isLessThan`, `isLessThanOrEqualTo`, and so on instead of `compareTo`?
## Answers
1. ![order log n](https://latex.codecogs.com/svg.latex?\Theta(\log&space;n))
1. Constant. This would happen if the first element of the array was they key being sought.
1.
    ```java
    /** Returns the first index at which key appears in a, or -1 if it does not. */
    public static int linearSearch(Object key, Object[] a) {
        for (int i = 0; i < a.length; i++) {
            if (a[i].equals(key)) {
                return i;
            }
        }
        return -1;
    }    
    ```
1. Yes, but for some algorithms (such as binary search) it could come at a performance cost. When a three-way comparison is needed (less than, equal, or greater than), using separate methods would require comparing the elements twice. If the comparison is very expensive (e.g., comparing String that represent long DNA sequences), this redundant work could waste significant time.
