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
## Binary Search
## Resources
## Questions
1. :star: What is the order of the worst-case running time of binary search?
1. :star::star: Complete the method below.
    ```java
    /** Returns the first index at which key appears in a, or -1 if it does not. */
    public static int linearSearch(Object key, Object[] a) {
      
    }
    ```
## Answers
1. ![order log n](https://latex.codecogs.com/svg.latex?\Theta(\log&space;n))
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
    
