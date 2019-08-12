# Algorithmic Strategies
## Algorithmic Problems
An *algorithmic problem* asks you to either devise a *function* or implement an *abstract data type* (using a data structure and one or more methods). Methods, like functions, have input and output; they may also depend on or mutate the associated data structure. You may run into such problems in a class, while solving a specific real-world problem, or while building code libraries for solving real-world problems.

A solution to an algorithmic problem should be:
- *Correct*. An incorrect solution is almost always useless, although there are some domains where approximate algorithms are acceptable.
- *Efficient*. The algorithm should use no more time or space (memory) than necessary. For small problems, this may make the difference between an algorithm that is pleasant to use and a painfully slow "memory hog". For large problems, an inefficient algorithm may demand so many resources that it is actually *unusable*.
- *Clear*. It is difficult to verify the correctness or efficiency of an algorithm that is not described or implemented clearly. Furthermore, people often need to adapt existing algorithms to new, slightly different problems; clarity makes this work easier.

It is important to distinguish a *problem* from a *problem instance*. Array sorting is a problem. Sorting a particular array of numbers is an instance of that problem. An algorithm that solves a problem can be run to solve any instance of that problem.

## Major Approaches

You will see many algorithms in your career as a computer scientist. Rather than view them as a disorganizes bag of tricks, it is useful to find some recurring themes. Here are four major approaches that you will encounter many times:

### Brute Force
Try all of the possibilities. For example, in searching for some element in an unordered array, you simply compare it to each element in the array. The brute force approach generally infeasible for problems involving combinations of elements.

### Transform
Turn the problem into an instance of a different problem, solve that, and turn the solution into a solution to the original problem. For example, when searching for an element in an array, sorting the array transforms the problem into an easier one.

### Divide and Conquer
Create two or more smaller instances, solve one or more of them, then use these solutions to solve the original instance. Binary search uses this approach, as do [recursive](../control_structures/recursion.md) algorithms.

### Incremental
Start with an easy guess at the solution and then improve it after each step. For example, to find the largest number in an array, you might first guess that it's the first element and then update this guess as you examine each successive element.

## Problem-Solving Strategy
## Resources
## Questions
## Answers
