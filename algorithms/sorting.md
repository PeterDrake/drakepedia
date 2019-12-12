# Sorting
## The Sorting Problem
## Comparables
## Insertion Sort
## Merge Sort
## Quicksort
## Heapsort
## Bucket Sort
## Resources
## Questions
1. :star: What is the order of the worst-case running time of insertion sort?
1. :star: What is the order of the running time of mergesort?
1. :star: What is the order of the worst-case running time of heapsort?
1. :star: When is insertion sort the best algorithm to use?
1. :star::star: Which sorting algorithm is this?
    ```java
    static void sort(int[] arr) {
        for (int i = 1; i < arr.length; i++) {
            for (int j = i; j > 0 && arr[j] < arr[j - 1]; j--) {
                int temp = arr[j];
                arr[j] = arr[j - 1];
                arr[j - 1] = temp;
            }
        }
    }
    ```
1. :star::star: How can quicksort be modified to make the worst case extremely unlikely?
1. :star::star: How does bucket sort beat the lower bound on sorting?
1. :star::star: Briefly explain the difference between insertion sort and selection sort.
## Answers
1. ![order n squared](https://latex.codecogs.com/svg.latex?\Theta(n^2))
1. ![order n log n](https://latex.codecogs.com/svg.latex?\Theta(n\log&space;n)), in both the best and worst case.
1. ![order n log n](https://latex.codecogs.com/svg.latex?\Theta(n\log&space;n)).
1. When sorting very short arrays or arrays that are already nearly sorted.
1. Insertion sort.
1. Shuffle the array before sorting.
1. It makes the additional assumption that the data are uniformly distributed across a known range. Since it uses arithmetic to place keys into buckets, it is not a comparison sort and the lower bound does not apply.
1. Insertion sort repeatedly finds the next item in the unsorted region and inserts it among the already sorted items. Selection sort repeatedly finds the smallest item among the unsorted items and adds it to the end of the sorted region.
