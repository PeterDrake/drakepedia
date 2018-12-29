# Analysis of Algorithms
## Timing
We often want to know how *efficient* an algorithm is, usually in terms of time. This can help answer questions such as:
- Which of these two algorithms is faster?
- Is this algorithm fast enough for our purposes?

A gross way to determine how much time an algorithm takes is to implement it and time it, using a stopwatch or using code like this:
```
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
### Orders
### Related Notations
## Analyzing Algorithms
### Iterative Algorithms
### Best-Case, Average-Case, Worst-Case, and Amortized Analysis
### Recursive Algorithms
## Additional Resources
### Online
- [Video lecture](https://www.youtube.com/watch?v=w7-6h64HSQ8) of this material
- OpenDSA, [Chapter 8](https://opendsa-server.cs.vt.edu/ODSA/Books/Everything/html/AnalChap.html)
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 4.1](https://introcs.cs.princeton.edu/java/41analysis/)
- Sedgewick and Wayne, *Algorithms, 4th Edition* booksite, [Section 1.4](https://algs4.cs.princeton.edu/14analysis/)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 4.1
- Sedgewick and Wayne, *Algorithms, 4th Edition*, Section 1.4
- Cormen *et al.*, *Introduction to Algorithms, 3rd Edition*, Chapters 3-4
## Questions
1. :star::star::star: Read the definition of ![tilde](https://latex.codecogs.com/svg.latex?\sim) notation on the Sedgewick & Wayne booksite. Given two functions ![f of n](https://latex.codecogs.com/svg.latex?f(n)) and ![g of n](https://latex.codecogs.com/svg.latex?g(n)), what is the relationship between the statements ![f of n tilde g of n](https://latex.codecogs.com/svg.latex?f(n)\sim&space;g(n)) and ![f of n is a member of big theta of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;\Theta(g(n)))? In other words, does one statement imply the other, vice versa, neither, or both?
## Answers
1. ![f of n tilde g of n](https://latex.codecogs.com/svg.latex?f(n)\sim&space;g(n)) implies ![f of n is a member of big theta of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;\Theta(g(n))), but not vice versa. For example, if ![f of n equals n](https://latex.codecogs.com/svg.latex?f(n)=n) and ![g of n equals 2n](https://latex.codecogs.com/svg.latex?g(n)=2n), then ![f of n is a member of big theta of g of n](https://latex.codecogs.com/svg.latex?f(n)\in&space;\Theta(g(n))) but it is not true that ![f of n tilde g of n](https://latex.codecogs.com/svg.latex?f(n)\sim&space;g(n)). The ![tilde](https://latex.codecogs.com/svg.latex?\sim) notation ignores lower-order terms just like ![big theta](https://latex.codecogs.com/svg.latex?\Theta) notation does, but it does not ignore constant factors.
