# Linked Lists
## Questions
1. :star: Write a Node class for building linked lists of doubles.
1. :star: Name an advantage linked lists have over arrays.
1. :star: What is the value of the `next` instance variable in the *last* Node in a linked list?
## Answers
1.  ```java
    class Node {
        double item;
        Node next;
    }
    ```
1. A linked list can grow longer or shorter. An array must have its length specified when it is created.
1. `null`.
