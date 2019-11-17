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

In the worst case, when `key` is either the last element or not present, this takes linear time. On average, assuming `key` is present and equally likely to be in any postion, about half of the elements have to be inspected, which still takes linear time.

## The Comparable Interface
It is possible to do better than linear search if the array is *sorted* in increasing order. This is only meaningful for arrays of types that can be compared to see if one value is larger than another. Clearly numbers can be compared. Strings can also be compared in *lexicographical order* (which is similar to alphabetical order, but accounts for with upper and lower case letters, digits, and other characters).

Rather than provide overloaded methods to account for every such type, you can use the built-in Comparable interface. Built-in classes like String and all of the wrapper classes implement Comparable. You could also implement it with your own classes.

Comparable has one method, `compareTo`. If `a` and `b` are instances of the same Comparable class, then `a.compareTo(b)` returns:
* a negative number if `a` is less than `b`,
* zero if `a` is equal to `b`, and
* a positive number if `a` is greater than `b`.

Don't try to read anything into the size of the returned number. Only the sign matters.

If you define your own Comparable class, be sure to define `equals` and `compareTo` consistently so that `a.equals(b)` returns true exactly when `a.compareTo(b)` returns zero.

## Binary Search

For a sorted array, the *binary search* algorithm starts by examining the *middle* element of the array. If it is equal to they key, its position is returned. Otherwise, binary search recursively searches either the left half of the array (if the key is less than the element examined) or the right half (otherwise). This continues until either the key is found or the region being searched shrinks to nothing (indicating that the key is not present).

Sedgewick and Wayne provide [an implementation](https://introcs.cs.princeton.edu/java/42sort/BinarySearch.java.html). Note that:
* The first version of `search` works calls the second, recursive version.
* This code only works for Strings, but it could be generalized by changing the parameter type from `String[]` to `Comparable[]`.

How long does binary search take in the worst case? An equivalent question is how many times the array length ![n](https://latex.codecogs.com/svg.latex?n) can be divided in half before getting down to 1. This is the definition of ![log base 2 of n](https://latex.codecogs.com/svg.latex?\log_2&space;n). The worst case running time of binary search is therefore in  ![order log n](https://latex.codecogs.com/svg.latex?\Theta(\log&space;n)).

The average running time is also logarithmic because about half of the array elements won't be examined until just before giving up (that is, after ![order log n](https://latex.codecogs.com/svg.latex?\Theta(\log&space;n)) comparisons).

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 4.2](https://introcs.cs.princeton.edu/java/42sort/)
- [Comparable](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Comparable.html) (Java API)

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
1. :star::star::star: To find the midpoint, Sedgewick and Wayne use the expression `lo + (hi - lo) / 2`. Wouldn't `(lo + hi) / 2` work just as well and be slightly more efficient?
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
1. Yes, but suppose the array is *very* large, `lo` is 1 billion, and `hi` is 2 billion. The intermediate value `(lo + hi)` would be 3 billion, which is too large to fit in an int. Sedgewick & Wayne's code avoids this issue.
