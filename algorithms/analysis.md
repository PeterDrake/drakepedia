# Analysis of Algorithms
## Timing
We often want to know how *efficient* an algorithm is, usually in terms of time. This can help answer questions such as:
- Which of these two algorithms is faster?
- Is this algorithm fast enough for our purposes?

For a gross estimate (or empirical verification), we can implement and algorithm and time it, using a stopwatch or using code like this:
```java
long before = System.currentTimeMillis();
// Run the algorithm to be timed
System.out.println((System.currentTimeMillis() - before) + " msec elapsed");
```
(`System.currentTimeMillis()` returns the number of milliseconds since [the beginning of 1970](https://en.wikipedia.org/wiki/Unix_time).)

There are a number of problems with this plan:
- The result may be affected by the programming language used, the speed of the physical machine, or other processes running on that machine. The last issue can be ameliorated by shutting down other programs such as web browsers, but a modern system often has dozens of processes running even when there are no other user programs running.
- Implementing an algorithm is difficult and time-consuming. We would prefer to know the result beforehand.
- The result is likely to depend on the size of the input. For example, it takes longer to sort a million numbers than ten.
- The result may depend on the specific input. For example, some algorithms take longer to sort a list of numbers that is currently in reverse order than a list in random order.

For these reasons, we turn to mathematical analysis tools such as asymptotic notation.
## Asymptotic Notation
### Running Time Functions
We can express the time taken by an algorithm as a function, such as ![3 n squared plus 2](https://latex.codecogs.com/svg.latex?3n^2&plus;2), where ![n](https://latex.codecogs.com/svg.latex?n) is the size of the input. Running the algorithm on larger inputs therefore takes more time.

In most cases it will be clear from context what ![n](https://latex.codecogs.com/svg.latex?n) means: the length of the array being sorted, the number of items stored in the data structure, etc. Running time functions usually take only one argument, but there are exceptions. Significantly, we express the running time for a graph algorithm in terms of ![v](https://latex.codecogs.com/svg.latex?v) (the number of vertices in the graph) and ![e](https://latex.codecogs.com/svg.latex?e) (the number of edges in the graph).
### Orders
Given the running time functions for two algorithms, which algorithm is faster? This question appears to open a huge can of mathematical worms, but there is a huge shortcut: asymptotic notation. This concerns what happens as ![n](https://latex.codecogs.com/svg.latex?n) becomes large.

Functions can be grouped into orders. An order is a set of functions. For example, ![big theta of n squared](https://latex.codecogs.com/svg.latex?\Theta(n^2)), pronounced "big theta of ![n squared](https://latex.codecogs.com/svg.latex?n^2)" or "order ![n squared](https://latex.codecogs.com/svg.latex?n^2)", is the set of functions that grow about like ![n squared](https://latex.codecogs.com/svg.latex?n^2). This set includes functions such as ![n squared](https://latex.codecogs.com/svg.latex?n^2), ![3 n squared plus 2](https://latex.codecogs.com/svg.latex?3n^2&plus;2), and ![5 n squared + 2 n + 12](https://latex.codecogs.com/svg.latex?5n^2&plus;2n&plus;12).

Orders are useful for two reasons:
- It is often relatively easy to tell which order a function is in.
- That is often enough information to tell which one grows more quickly.

To tell what order a function is in, we take advantage of two rules:
1. Adding or subtracting a term from a lower order doesn't matter.
1. Multiplying by a positive constant factor doesn't matter.

For example, the first rule tells us that ![5 n squared + 2 n + 12](https://latex.codecogs.com/svg.latex?5n^2&plus;2n&plus;12) is in the same order as ![5 n squared](https://latex.codecogs.com/svg.latex?5n^2), because the lower-order terms ![2 n](https://latex.codecogs.com/svg.latex?2n) and ![12](https://latex.codecogs.com/svg.latex?12) don't matter. When ![n](https://latex.codecogs.com/svg.latex?n) is large, these terms will be vanishingly small compared to ![5 n squared](https://latex.codecogs.com/svg.latex?5n^2).

The second rule tells us that ![5 n squared](https://latex.codecogs.com/svg.latex?5n^2) is in ![order n squared](https://latex.codecogs.com/svg.latex?\Theta(n^2)), because the constant factor ![5](https://latex.codecogs.com/svg.latex?5) doesn't matter. Ignoring the constant factor means that our analysis doesn't depend on details like the speed of the hardware: if an algorithm takes time in ![order n squared](https://latex.codecogs.com/svg.latex?\Theta(n^2)), that won't change if we run it on a machine that is twice as fast.

If we know what orders two functions are in, it's easy to compare them. For example, suppose:

![f of n is in order n squared and g of n is in order n cubed](https://latex.codecogs.com/svg.latex?\begin{aligned}f(n)\in\Theta(n^2)\\\\g(n)\in\Theta(n^3)\end{aligned})

Clearly, ![g of n](https://latex.codecogs.com/svg.latex?g(n)) is larger for large ![n](https://latex.codecogs.com/svg.latex?n). We would therefore prefer an algorithm whose running time is ![f of n](https://latex.codecogs.com/svg.latex?f(n)), because it takes less time on large inputs.

The table below summarizes the most commonly occurring orders, with preferable (smaller) orders at the bottom.

Order | Nickname
--|--
![order 2 to the n](https://latex.codecogs.com/svg.latex?2^n) | exponential
![order n cubed](https://latex.codecogs.com/svg.latex?n^3) | cubic
![order n squared](https://latex.codecogs.com/svg.latex?n^2) | quadratic
![order n log n](https://latex.codecogs.com/svg.latex?n\log&space;n) | linearithmic
![order n](https://latex.codecogs.com/svg.latex?n) | linear
![order log n](https://latex.codecogs.com/svg.latex?\log&space;n) | logarithmic
![order 1](https://latex.codecogs.com/svg.latex?1) | constant

### Related Notations
There are several related asymptotic notations referring to unions of multiple orders. For example, the set ![big o of n](https://latex.codecogs.com/svg.latex?O(n)), pronounced "big O of ![n](https://latex.codecogs.com/svg.latex?n)", is the union of ![order n](https://latex.codecogs.com/svg.latex?\Theta(n)) and all lower orders. If we say that a function is in ![big o of n](https://latex.codecogs.com/svg.latex?O(n)), we mean that it is in ![order n](https://latex.codecogs.com/svg.latex?\Theta(n)) or some lower order.

The related notations are summarized in the table below. Note that ![big omega](https://latex.codecogs.com/svg.latex?\Omega(n)) and ![little omega](https://latex.codecogs.com/svg.latex?\omega(n)) are the upper- and lower-case versions of the Greek letter omega.

Notation | Idea | Combines | ![f](https://latex.codecogs.com/svg.latex?f) grows
-|-|-|-
![f is in little omega of g](https://latex.codecogs.com/svg.latex?f\in&space;\omega(g)) | ![big theta of f is greater than big theta of g](https://latex.codecogs.com/svg.latex?\Theta(f)>\Theta(g)) | orders higher than ![order g](https://latex.codecogs.com/svg.latex?\Theta(g)) | much more quickly than ![g](https://latex.codecogs.com/svg.latex?g)

## Analyzing Algorithms
### Non-Recursive Algorithms
### Best-Case, Average-Case, Worst-Case, and Amortized Analysis
### Recursive Algorithms
## Additional Resources
### Online
- Short [video lecture](https://www.youtube.com/watch?v=w7-6h64HSQ8) on asymptotic notation
- OpenDSA, [Chapter 8](https://opendsa-server.cs.vt.edu/ODSA/Books/Everything/html/AnalChap.html)
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 4.1](https://introcs.cs.princeton.edu/java/41analysis/)
- Sedgewick and Wayne, *Algorithms, 4th Edition* booksite, [Section 1.4](https://algs4.cs.princeton.edu/14analysis/)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 4.1
- Sedgewick and Wayne, *Algorithms, 4th Edition*, Section 1.4
- Cormen *et al.*, *Introduction to Algorithms, 3rd Edition*, Chapters 3-4
## Questions
1. TODO Cases where other asymptotic notations are or are not sufficient to determine which algorithm is faster
1. TODO Deceptive big O result due to constant > 1
1. :star::star::star: Read the definition of ![tilde](https://latex.codecogs.com/svg.latex?\sim) notation on the Sedgewick & Wayne booksite. Given two functions ![f of n](https://latex.codecogs.com/svg.latex?f(n)) and ![g of n](https://latex.codecogs.com/svg.latex?g(n)), what is the relationship between the statements ![f of n tilde g of n](https://latex.codecogs.com/svg.latex?f(n)\sim&space;g(n)) and ![f of n is in big theta of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;\Theta(g(n)))? In other words, does one statement imply the other, vice versa, neither, or both?
## Answers
1.
1.
1. ![f of n tilde g of n](https://latex.codecogs.com/svg.latex?f(n)\sim&space;g(n)) implies ![f of n is in big theta of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;\Theta(g(n))), but not vice versa. For example, if ![f of n equals n](https://latex.codecogs.com/svg.latex?f(n)=n) and ![g of n equals 2n](https://latex.codecogs.com/svg.latex?g(n)=2n), then ![f of n is in big theta of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;\Theta(g(n))) but it is not true that ![f of n tilde g of n](https://latex.codecogs.com/svg.latex?f(n)\sim&space;g(n)). The ![tilde](https://latex.codecogs.com/svg.latex?\sim) notation ignores lower-order terms just like ![big theta](https://latex.codecogs.com/svg.latex?\Theta) notation does, but it does not ignore constant factors.
