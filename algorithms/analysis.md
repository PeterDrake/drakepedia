# Analysis of Algorithms
## Timing
We often want to know how *efficient* an algorithm is, usually in terms of time. This can help answer questions such as:
- Which of these two algorithms is faster?
- Is this algorithm fast enough for our purposes?

For a gross estimate (or empirical verification), we can implement an algorithm and time it, using a stopwatch or using code like this:
```java
long before = System.currentTimeMillis();
// Run the algorithm to be timed
System.out.println((System.currentTimeMillis() - before) + " msec elapsed");
```
(`System.currentTimeMillis()` returns the number of milliseconds since [the beginning of 1970](https://en.wikipedia.org/wiki/Unix_time).)

There are a number of problems with this approach:
- The result may be affected by the programming language used, the speed of the physical machine, or other processes running on that machine. The last issue can be ameliorated by shutting down other programs such as web browsers, but a modern system often has dozens of processes running even when there are no other user programs running.
- Implementing an algorithm is difficult and time-consuming. We would prefer to know the result beforehand.
- The result is likely to depend on the size of the input. For example, it takes longer to sort a million numbers than ten.
- The result may depend on the specific input. For example, some algorithms take longer to sort a list of numbers that is currently in reverse order than a list in random order.

For these reasons, we turn to mathematical analysis tools such as asymptotic notation.
## Asymptotic Notation
### Running Time Functions
We can express the time taken by an algorithm as a function, such as ![3 n squared plus 2](https://latex.codecogs.com/svg.latex?3n^2+2), where ![n](https://latex.codecogs.com/svg.latex?n) is the size of the input. Running an algorithm on larger inputs generally takes more time.

In most cases it will be clear from context what ![n](https://latex.codecogs.com/svg.latex?n) means: the length of the array being sorted, the number of items stored in the data structure, etc. Running time functions usually take only one argument, but there are exceptions. Significantly, we express the running time for a graph algorithm in terms of ![v](https://latex.codecogs.com/svg.latex?v) (the number of vertices in the graph) and ![e](https://latex.codecogs.com/svg.latex?e) (the number of edges in the graph).
### Orders
Given the running time functions for two algorithms, which algorithm is faster? This question appears to open a can of mathematical worms, but there is a huge shortcut: asymptotic notation. This concerns what happens as ![n](https://latex.codecogs.com/svg.latex?n) becomes large.

Functions can be grouped into orders. An order is a set of functions. For example, ![big theta of n squared](https://latex.codecogs.com/svg.latex?\Theta(n^2)), pronounced "big theta of ![n squared](https://latex.codecogs.com/svg.latex?n^2)" or "order ![n squared](https://latex.codecogs.com/svg.latex?n^2)", is the set of functions that grow about like ![n squared](https://latex.codecogs.com/svg.latex?n^2). This set includes functions such as ![n squared](https://latex.codecogs.com/svg.latex?n^2), ![3 n squared plus 2](https://latex.codecogs.com/svg.latex?3n^2+2), and ![5 n squared plus 2 n plus 12](https://latex.codecogs.com/svg.latex?5n^2+2n+12).

The table below summarizes the most commonly occurring orders.

Order | Nickname
--|--
![order 2 to the n](https://latex.codecogs.com/svg.latex?\Theta(2^n)) | exponential
![order n cubed](https://latex.codecogs.com/svg.latex?\Theta(n^3)) | cubic
![order n squared](https://latex.codecogs.com/svg.latex?\Theta(n^2)) | quadratic
![order n log n](https://latex.codecogs.com/svg.latex?\Theta(n\log&space;n)) | linearithmic
![order n](https://latex.codecogs.com/svg.latex?\Theta(n)) | linear
![order log n](https://latex.codecogs.com/svg.latex?\Theta(\log&space;n)) | logarithmic
![order 1](https://latex.codecogs.com/svg.latex?\Theta(1)) | constant

Orders are useful for two reasons:
- It is often relatively easy to tell which order a function is in.
- That is often enough information to tell which one grows more quickly.

To tell what order a function is in, we take advantage of two rules:
1. Adding or subtracting a term from a lower order doesn't matter.
1. Multiplying by a positive constant factor doesn't matter.

For example, the first rule tells us that ![5 n squared + 2 n + 12](https://latex.codecogs.com/svg.latex?5n^2+2n+12) is in the same order as ![5 n squared](https://latex.codecogs.com/svg.latex?5n^2), because the lower-order terms ![2 n](https://latex.codecogs.com/svg.latex?2n) and ![12](https://latex.codecogs.com/svg.latex?12) don't matter. When ![n](https://latex.codecogs.com/svg.latex?n) is large, these terms are vanishingly small compared to ![5 n squared](https://latex.codecogs.com/svg.latex?5n^2).

The second rule tells us that ![5 n squared](https://latex.codecogs.com/svg.latex?5n^2) is in ![order n squared](https://latex.codecogs.com/svg.latex?\Theta(n^2)), because the constant factor ![5](https://latex.codecogs.com/svg.latex?5) doesn't matter. Ignoring the constant factor means that our analysis doesn't depend on details like the speed of the hardware; if an algorithm takes time in ![order n squared](https://latex.codecogs.com/svg.latex?\Theta(n^2)), that won't change if we run it on a machine that is twice as fast.

If we know what orders two functions are in, it's easy to compare them. For example, suppose:

![f of n is in order n squared and g of n is in order n cubed](https://latex.codecogs.com/svg.latex?\begin{aligned}f(n)\in\Theta(n^2)\\\\g(n)\in\Theta(n^3)\end{aligned})

Clearly, ![g of n](https://latex.codecogs.com/svg.latex?g(n)) is larger for large ![n](https://latex.codecogs.com/svg.latex?n). We would therefore prefer an algorithm whose running time is ![f of n](https://latex.codecogs.com/svg.latex?f(n)), because it takes less time on large inputs.

### Related Notations
There are several related asymptotic notations referring to unions of multiple orders. For example, the set ![big o of n](https://latex.codecogs.com/svg.latex?O(n)), pronounced "big O of ![n](https://latex.codecogs.com/svg.latex?n)", is the union of ![order n](https://latex.codecogs.com/svg.latex?\Theta(n)) and all lower orders. If we say that a function is in ![big o of n](https://latex.codecogs.com/svg.latex?O(n)), we mean that it is in ![order n](https://latex.codecogs.com/svg.latex?\Theta(n)) or some lower order.

The related notations are summarized in the table below. Phrasing such as "much more" or "about like" is meant to emphasize that there is a constant factor of "wiggle room" within a given order.

Notation | Pronounced | Idea | Combines | ![f](https://latex.codecogs.com/svg.latex?f) Grows
-|-|-|-|-
![f is in big omega of g](https://latex.codecogs.com/svg.latex?f\in&space;\Omega(g)) | ![f](https://latex.codecogs.com/svg.latex?f) is in big omega of ![g](https://latex.codecogs.com/svg.latex?g) | ![big theta of f is greater than or equal to big theta of g](https://latex.codecogs.com/svg.latex?\Theta(f)\geq\Theta(g)) | ![order g](https://latex.codecogs.com/svg.latex?\Theta(g)) and higher orders | like ![g](https://latex.codecogs.com/svg.latex?g) or much more quickly
![f is in big theta of g](https://latex.codecogs.com/svg.latex?f\in&space;\Theta(g))  | ![f](https://latex.codecogs.com/svg.latex?f) is in big theta of ![g](https://latex.codecogs.com/svg.latex?g)| ![big theta of f equals big theta of g](https://latex.codecogs.com/svg.latex?\Theta(f)=\Theta(g)) | ![order g](https://latex.codecogs.com/svg.latex?\Theta(g)) | about like ![g](https://latex.codecogs.com/svg.latex?g)
![f is in big o of g](https://latex.codecogs.com/svg.latex?f\in&space;O(g))  | ![f](https://latex.codecogs.com/svg.latex?f) is in big o of ![g](https://latex.codecogs.com/svg.latex?g)| ![big theta of f is less than or equal to big theta of g](https://latex.codecogs.com/svg.latex?\Theta(f)\leq\Theta(g)) | ![order g](https://latex.codecogs.com/svg.latex?\Theta(g)) and lower orders | like ![g](https://latex.codecogs.com/svg.latex?g) or much more slowly

## Analyzing Algorithms
### Non-Recursive Algorithms
Any operation whose time doesn't depend on the size of its input takes constant time. This includes assignments and arithmetic operations on primitive numbers (which are of bounded size).

To analyze a non-recursive algorithm, ask of each step:
- How long does this step take?
- How many times is this step executed?

Multiplying these two values gives the total time cost of that step. The time for the entire algorithm is the sum of these costs.

For example, consider this method:
```java
static int sum(int n) {
    int sum;
    sum = 0;
    int i;
    i = 1;
    while (i <= n) {
        sum += i;
        i++;
    }
    return sum;
}
```
Analyzing this line-by-line, we assign a lettered constant for the amount of time taken by each step. We don't know exactly how long each step takes and, because we only need to know the order of the result, we don't care.

Line | Cost | Times | Total
-|-|-|-
`int sum;` | ![a](https://latex.codecogs.com/svg.latex?a) | 1 | ![a](https://latex.codecogs.com/svg.latex?a)
`sum = 0;` | ![b](https://latex.codecogs.com/svg.latex?b) | 1 | ![b](https://latex.codecogs.com/svg.latex?b)
`int i;` | ![c](https://latex.codecogs.com/svg.latex?c) | 1 | ![c](https://latex.codecogs.com/svg.latex?c)
`i = 1;` | ![d](https://latex.codecogs.com/svg.latex?d) | 1 | ![d](https://latex.codecogs.com/svg.latex?d)
`while (i <= n)` | ![e](https://latex.codecogs.com/svg.latex?e) | ![n plus 1](https://latex.codecogs.com/svg.latex?n+1) | ![e n plus e](https://latex.codecogs.com/svg.latex?en+e)
`sum += 1;` | ![f](https://latex.codecogs.com/svg.latex?f) | ![n](https://latex.codecogs.com/svg.latex?n) | ![f n](https://latex.codecogs.com/svg.latex?fn)
`i++;` | ![g](https://latex.codecogs.com/svg.latex?g) | ![n](https://latex.codecogs.com/svg.latex?n) | ![g n](https://latex.codecogs.com/svg.latex?gn)
`return sum;` | ![h](https://latex.codecogs.com/svg.latex?h) | 1 | ![h](https://latex.codecogs.com/svg.latex?h)

This adds up to:

![a plus b plus c plus d plus e n plus e plus f n plus g n plus h](https://latex.codecogs.com/svg.latex?a+b+c+d+en+e+fn+gn+h)

Since lower order terms don't matter, this in the same order as

![e n plus f n plus g n, which is equal to the sum of e, f, ang g multiplied by n](https://latex.codecogs.com/svg.latex?en+fn+gn=(e+f+g)n)

which is in ![order n](https://latex.codecogs.com/svg.latex?\Theta(n)).

This technique works, but with practice we can often simply find the step that, taking into account how many times it runs, is the most expensive. All other steps are in the same order or lower orders, so they don't matter.

One subtlety to watch out for: one line of code may involve multiple steps, especially if it includes a method call.

### Best-Case, Average, Worst-Case, and Amortized Analysis
Consider this method:
```java
static boolean linearSearch(int key, int[] a) {
    for (int i = 0; i < a.length; i++) {
        if (a[i] == key) {
            return true;
        }
    }
    return false;
}
```
The number of times the loop runs depends not just on ![n](https://latex.codecogs.com/svg.latex?n) (the length of the array `a`) but also on the *contents* of `a`. In a situation like this, we must clarify whether a statement is about best-case, average, or worst-case performance.

Suppose `key` is present in `a` at exactly one place. In the best case, `key` is at index 0, so the loop only runs once. We can say that this algorithm takes constant time in the best case.

In the worst case, `key` is in the last position (index ![n minus 1](https://latex.codecogs.com/svg.latex?n-1)), so the algorithm takes linear time.

Average case analysis can be a bit trickier, because we have to make additional assumptions about how likely various possibilities are. For this algorithm, let's assume that `key` is equally likely to be at any position in the array. The average number of passes through the loop is therefore:

![1 over n times the sum of the numbers 1 through n, which equals n plus 1 over 2, which is in order n](https://latex.codecogs.com/svg.latex?\frac{1}{n}\sum_{i=1}^n{i}=\frac{n+1}{2}\in\Theta(n))

The best-case running time of an algorithm is always at least as good as its average running time, which in turn is at least as good as its worst-case running time.

On some occasions we will do amortized analysis, which asks, "What's the average behavior over the worst possible sequence of operations?" For almost all algorithms, this is exactly the same as worst-case analysis, because the worst possible sequence of operations is just the worst individual operation over and over again. For some data structures (notably resizable arrays) the worst operation *can't* happen over and over again, so the amortized result may be better. Amortized running time is always at least as good as worst-case and at least as bad as average.

In summary:

Analysis | Question Answered
-|-
Worst-case | How long will this take for the worst individual operation?
Amortized | How long will this take per operation for the worst sequence of operations?
Average | How long will this take per operation over a typical sequence of operations?
Best-case | How long will this take for the best individual operation?

### Recursive Algorithms
Here is a recursive algorithm for summing the numbers in an array, implemented as two methods:
```java
static double sum(double[] a) {
    return sum(a, 0);
}

static double sum(double[] a, int i) {
    if (i == a.length - 1) {
        return a[i];
    }
    return a[i] + sum(a, i + 1);
}
```
What is the order of its running time? The non-recursive method does nothing but call the other one and return the result, so it is the second method we must examine. Our normal technique doesn't work because it's not clear how long the recursive call takes.

To analyze a recursive algorithm, we first write a special equation called a recurrence relation. For this algorithm, the recurrence relation is:

![t of n is 1 if n equals 1, or 1 plus t of n minus one otherwise](https://latex.codecogs.com/svg.latex?T(n)=\begin{cases}1\textrm{&space;if&space;}n=1\\\\1+T(n-1)\textrm{&space;otherwise}\end{cases})

The upper part says that the time to process ![n](https://latex.codecogs.com/svg.latex?n) numbers is constant in the base case where ![n is 1](https://latex.codecogs.com/svg.latex?n=1). It won't matter what the constant is, so we choose ![1](https://latex.codecogs.com/svg.latex?1) for simplicity.

The lower part says that, in the recursive case, the time is a constant plus the time to process ![n minus 1](https://latex.codecogs.com/svg.latex?n-1) elements.

To get to an order, we need to solve the recurrence relation, that is, find an equivalent closed form equation that doesn't have ![t of n](https://latex.codecogs.com/svg.latex?T(n)) on the right side. In this case the solution is:

![t of n equals n](https://latex.codecogs.com/svg.latex?T(n)=n)

This can be verified by substituting the solution into the recurrence relation.

Solving recurrence relations is an advanced topic, but fortunately a few specific cases cover most of the recursive algorithms you'll encounter. They are summarized in the table below, which omits the base case lines as they don't affect the order of the solutions.

Recurrence | Solution Order
-|-
![t of n equals n plus t of n minus 1](https://latex.codecogs.com/svg.latex?T(n)=n+T(n-1)) | ![order n squared](https://latex.codecogs.com/svg.latex?\Theta(n^2))
![t of n equals n plus 2 times t of n over 2](https://latex.codecogs.com/svg.latex?T(n)=n+2T(n/2)) | ![order n log n](https://latex.codecogs.com/svg.latex?\Theta(n\log&space;n))
![t of n equals 1 plus t of n minus 1](https://latex.codecogs.com/svg.latex?T(n)=1+T(n-1)) | ![order n](https://latex.codecogs.com/svg.latex?\Theta(n))
![t of n equals n plus t of n over 2](https://latex.codecogs.com/svg.latex?T(n)=n+T(n/2)) | ![order n](https://latex.codecogs.com/svg.latex?\Theta(n))
![t of n equals 1 plus t of n over 2](https://latex.codecogs.com/svg.latex?T(n)=1+T(n/2)) | ![order log n](https://latex.codecogs.com/svg.latex?\Theta(\log&space;n))

## Resources
### Online
- Short [video lecture](https://www.youtube.com/watch?v=w7-6h64HSQ8) on asymptotic notation
- OpenDSA, [Algorithm Analysis](https://opendsa-server.cs.vt.edu/ODSA/Books/Everything/html/AnalChap.html)
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 4.1](https://introcs.cs.princeton.edu/java/41analysis/)
- Sedgewick and Wayne, *Algorithms, 4th Edition*, [Section 1.4](https://algs4.cs.princeton.edu/14analysis/)
- Cormen *et al.*, *Introduction to Algorithms, 3rd Edition*, Chapters 3-4
- [Big-O Emoji](https://devrant.com/rants/1858258/big-o-emoji)

## Questions
1. :star::star: What's wrong with the following statement?
   > Since ![n cubed](https://latex.codecogs.com/svg.latex?n^3) grows more quickly than ![n squared](https://latex.codecogs.com/svg.latex?n^2), an algorithm with cubic running time is faster than one with quadratic running time.
1. :star::star: Suppose we know that ![f of n is in big o of n squared](https://latex.codecogs.com/svg.latex?f(n)\in&space;O(n^2)), ![g of n is in big o of n cubed](https://latex.codecogs.com/svg.latex?g(n)\in&space;O(n^3)), and ![h of n is in big omega of n cubed](https://latex.codecogs.com/svg.latex?h(n)\in&space;\Omega(n^3)).
   1. What can we conclude about the relationship between ![the order of f of n](https://latex.codecogs.com/svg.latex?\Theta(f(n))) and ![the order of g of n](https://latex.codecogs.com/svg.latex?\Theta(g(n)))?
   1. What can we conclude about the relationship between ![the order of f of n](https://latex.codecogs.com/svg.latex?\Theta(f(n))) and ![the order of h of n](https://latex.codecogs.com/svg.latex?\Theta(h(n)))?
   1. What can we conclude about the relationship between ![the order of g of n](https://latex.codecogs.com/svg.latex?\Theta(g(n))) and ![the order of h of n](https://latex.codecogs.com/svg.latex?\Theta(h(n)))?
1. :star::star: Suppose we know that ![f of n is in big o of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;O(g(n))). Can we conclude that ![f of n is less than or equal to g of n](https://latex.codecogs.com/svg.latex?f(n)\leq&space;g(n)) for small values of ![n](https://latex.codecogs.com/svg.latex?n)? What about for large values?
1. :star::star: What is the order of the running time of the `linearSearch` algorithm above when `key` is not present in `a`?
1. :star::star: What's wrong with the following statement?
   > The best case for the algorithm I'm analyzing occurs when ![n equals 1](https://latex.codecogs.com/svg.latex?n=1).
1. :star::star: What is the order of the worst-case running time of the method below?
    ```java
    static boolean mystery(int[] arr, int k) {
        int lo = 0;
        int hi = arr.length;
        while (lo < hi) {
            if (arr[lo] == k) {
                return true;
            }
            lo++;
        }
        return false;
    }
    ```
1. :star::star: What is the order of the running time of the code below?
    ```java
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            System.out.println(i + ", " + j);
        }
    }
    ```
1. :star::star: What is the order of the running time of the code below?
    ```java
    for (int i = n; i > 0; i /= 2) {
        System.out.println(n);
    }
    ```
1. :star::star::star: What statement in asymptotic notation is equivalent to the following?
   > There exists some ![c greater than 0](https://latex.codecogs.com/svg.latex?c>0) and some ![n sub zero](https://latex.codecogs.com/svg.latex?n_0) such that, for all ![n greater than or equal to n sub zero](https://latex.codecogs.com/svg.latex?n\geq&space;n_0), ![f of n is less than or equal to c times g of n](https://latex.codecogs.com/svg.latex?f(n)\leq&space;cg(n)).
1. :star::star::star: Read the definition of ![tilde](https://latex.codecogs.com/svg.latex?\sim) notation on the Sedgewick & Wayne booksite. Given two functions ![f(n)](https://latex.codecogs.com/svg.latex?f(n)) and ![g of n](https://latex.codecogs.com/svg.latex?g(n)), what is the relationship between the statements ![f of n tilde g of n](https://latex.codecogs.com/svg.latex?f(n)\sim&space;g(n)) and ![f of n is in big theta of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;\Theta(g(n)))? In other words, does one statement imply the other, vice versa, neither, or both?
1. :star::star::star: The notation ![f is in big o of g](https://latex.codecogs.com/svg.latex?f\in&space;O(g)) means that ![f](https://latex.codecogs.com/svg.latex?f) is either in the same order as ![g](https://latex.codecogs.com/svg.latex?g) or a lower order. Is there a notation that means ![f](https://latex.codecogs.com/svg.latex?f) is in a strictly lower order?
## Answers
1. If the running time grows quickly, then it is very large for large values of ![n](https://latex.codecogs.com/svg.latex?n). To have a large running time is to be slow.
1.
   1. Nothing.
   1. ![the order of f of n](https://latex.codecogs.com/svg.latex?\Theta(f(n))) is a lower order than ![the order of h of n](https://latex.codecogs.com/svg.latex?\Theta(h(n))).
   1. Either ![the order of g of n](https://latex.codecogs.com/svg.latex?\Theta(g(n))) is a lower order than ![the order of h of n](https://latex.codecogs.com/svg.latex?\Theta(h(n))) or they are both the same order, namely ![order n cubes](https://latex.codecogs.com/svg.latex?\Theta(n^3)).
1. No. Asymptotic notation says nothing about small values of ![n](https://latex.codecogs.com/svg.latex?n). For large values, we know that ![f of n](https://latex.codecogs.com/svg.latex?f(n)) exceeds ![g of n](https://latex.codecogs.com/svg.latex?g(n)) by no more than a constant factor, but it might be that ![f of n equals 10 n](https://latex.codecogs.com/svg.latex?f(n)=10n) and ![g of n equals n](https://latex.codecogs.com/svg.latex?g(n)=n).
1. Linear.
1. Best-case, average, amortized, and worst-case analysis must apply for all values of ![n](https://latex.codecogs.com/svg.latex?n). If they differ, they must do so between different inputs of each size. For example, a sorting algorithm might have a best case when the array is already sorted and a worst case when it is already sorted in reverse order.
1. ![order n](https://latex.codecogs.com/svg.latex?\Theta(n)). In the worst case, the loop examines each of the ![n](https://latex.codecogs.com/svg.latex?n) elements of `arr`.
1. ![order n squared](https://latex.codecogs.com/svg.latex?\Theta(n^2)). The innermost line takes constant time. The inner loop runs ![n](https://latex.codecogs.com/svg.latex?n) times each time the outer loop runs. The outer loop runs ![n](https://latex.codecogs.com/svg.latex?n) times, so the innermost line runs a total of ![n squared](https://latex.codecogs.com/svg.latex?n^2) times.
1. ![order log n](https://latex.codecogs.com/svg.latex?\Theta(\log&space;n))
1. ![f of n is in big o of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;O(g(n)))
1. ![f of n tilde g of n](https://latex.codecogs.com/svg.latex?f(n)\sim&space;g(n)) implies ![f of n is in big theta of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;\Theta(g(n))), but not vice versa. For example, if ![f of n equals n](https://latex.codecogs.com/svg.latex?f(n)=n) and ![g of n equals 2n](https://latex.codecogs.com/svg.latex?g(n)=2n), then ![f of n is in big theta of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;\Theta(g(n))) but it is not true that ![f of n tilde g of n](https://latex.codecogs.com/svg.latex?f(n)\sim&space;g(n)). The ![tilde](https://latex.codecogs.com/svg.latex?\sim) notation ignores lower-order terms just like ![big theta](https://latex.codecogs.com/svg.latex?\Theta) notation does, but it does not ignore constant factors.
1. Yes: ![f is in little o of g](https://latex.codecogs.com/svg.latex?f\in&space;o(g)). Similarly, ![f is in little omega of g](https://latex.codecogs.com/svg.latex?f\in&space;\omega(g)), where ![the symbol that looks like a w](https://latex.codecogs.com/svg.latex?\omega) is a lower-case omega, means that ![f](https://latex.codecogs.com/svg.latex?f) is in a strictly higher order.
