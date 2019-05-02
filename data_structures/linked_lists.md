# Linked Lists
## Questions
1. :star: Write a Node class for building linked lists of doubles.
1. :star: Name an advantage linked lists have over arrays.
1. :star: What is the value of the `next` instance variable in the *last* Node in a linked list?
1. :star::star: The method below is supposed to determine the length of a linked list, but it has an off-by-one error. How should it be fixed?
    ```java
    public int length() {
        int result = 0;
        for (Node n = front.next; n != null; n = n.next) {
            result++;
        }
        return result;
    }
    ```
## Answers
1.  ```java
    class Node {
        double item;
        Node next;
    }
    ```
1. A linked list can grow longer or shorter. An array must have its length specified when it is created.
1. `null`.
1. `n` should start at `front`, not `front.next`.
