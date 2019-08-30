# Linked Lists
## Overview
One way to represent a sequence of items is an [array](arrays.md). Another is a *linked list*, which is a chain of Node objects, each of which contains one item and a [reference](references.md) to the next Node.

![list contains a reference to a node. That node contains 5 and a reference to the next node. The second node contains 2 and a reference to the third node. The third node contains 3 and a null reference.](linked_list.svg)

If you have defined the Node class as

```java
class Node {
    int item;
    Node next;
}
```

then the list in the diagram above could be created by the following code:

```java
Node a = new Node();
a.item = 5;
Node b = new Node();
b.item = 2;
Node c = new Node();
c.item = 3;
a.next = b;
b.next = c;
Node list = a;
```

(The temporary variables `a`, `b`, and `c` are not shown in the diagram.) Note that `c`'s `next` instance variable is left at its default value of `null`. The value `null` is also used to represent an empty linked list (one containing no items).



## Resources
## Questions

1. :star: Write a Node class for building linked lists of doubles.
1. :star: Name an advantage linked lists have over arrays.
1. :star: What is the value of the `next` instance variable in the *last* Node in a linked list?
1. :star::star: The method below is supposed to determine the length of a linked list, but it contains an off-by-one error. How should it be fixed?
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
