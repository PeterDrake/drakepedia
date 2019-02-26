# Recursion
## Overview
A *recursive* method is one that calls itself. This is useful for algorithms that can naturally be expressed in terms of solving a problem by first solving an easier problem.

For example, suppose we want to compute ![n followed by an exclamation point](https://latex.codecogs.com/svg.latex?n!) (pronounced "![n](https://latex.codecogs.com/svg.latex?n) factorial"), which is the product of the first ![n](https://latex.codecogs.com/svg.latex?n) positive integers.

Here is a recursive solution:

```java
static int factorial(int n) {
    if (n == 1) {
        return 1;
    }
    return factorial(n - 1) * n;
}
```

The first part, called the *base case*, directly solves a simple problem: ![1 factorial is 1](https://latex.codecogs.com/svg.latex?n!=1).

The second part, the *recursive case*, solves the simpler problem of computing ![n minus 1 factorial](https://latex.codecogs.com/svg.latex?(n-1)!), then multiplies that result by [n](https://latex.codecogs.com/svg.latex?n) to find [n factorial](https://latex.codecogs.com/svg.latex?n!).

This may seem like a strange way to solve the problem. You should be able to devise a less confusing (and slightly more efficient) algorithm to find the same result using *iteration* (a loop). In fact, anything that can be done with iteration can be done with recursion, and vice versa.

Why, then, should you wrap your head around recursion? Some algorithms are much more naturally expressed using recursion. For example, consider the Towers of Hanoi puzzle, which seeks to move `n` disks from peg `start` to peg `end`, using peg `spare` for temporary storage. A *divide and conquer* algorithm first recursively moves `n - 1` disks to `spare`, then moves the largest disk to `end`, and finally recursively moves `n - 1` disks from `spare` to `end`.

```java
static void hanoi(String start, String spare, String end, int n) {
    if (n == 1) {
        System.out.println(start + " -> " + end);
    } else {
        hanoi(start, end, spare, n - 1);
        System.out.println(start + " -> " + end);
        hanoi(spare, start, end, n - 1);
    }
}
```

Solving this problem using iteration would be considerably more difficult.

## Additional Resources
### Online
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 2.3](https://introcs.cs.princeton.edu/java/23recursion/)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 2.3
## Questions
1. :star: What happens if a recursive method with no base case is called?
1. :star: When is recursion preferable to iteration (using loops)?
## Answers
1. It keeps calling itself until the call stack fills up all available memory, at which point the program crashes. This is called a stack overflow.
1. Some algorithms are much more clearly stated using recursion rather than iteration. These are algorithms that solve a problem by first solving one or more easier problems. In general, if you can find a way to express your algorithm iteratively, do that; if, in trying to do this, you find that you need to remember work to do after solving the easier problem, recursion will probably be easier.
