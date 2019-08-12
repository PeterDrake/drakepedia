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

If you are overwhelmed by an algorithmic problem, or find that your thoughts are disorganized, the following checklist may help.

1. Carefully examine the problem description
    - What are the inputs, outputs, and (for an absract data type problem) data mutations?
    - Define several test cases, representing all major categories of inputs.
    - What is important to the computation and what can be abstracted away?
    - Is this identical or similar to another problem for which a solution is known?
1. Devise several plans
    - Apply the approaches above to brainstorm plans.
    - Describe each plan in pseudocode.
1. Analyze plans
    - Determine the order of the running time of each plan.
    - Eliminate clearly inferior plans.
1. Carry out each plan
    - Write unit tests to verify that code is correct.
    - Write the code.
    - Beautify and, if necessary, optimize the code.
1. Analyze results
    - Time each implementation to verify the analysis.
    - Reflect on what you've learned, both about this problem and in general.
1. Present results
    - Clearly explain all of the previous steps.
    
## Resources

## Questions
## Answers
