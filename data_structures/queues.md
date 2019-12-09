# Queues
## Abstract Data Type

A *queue* (pronounced like the letter Q) is similar to a stack, but items are added at one end (the back) and removed from the other (the front). The metaphor is a line of people waiting to buy tickets: new people arrive at the back and (after buying their tickets) leave from the front. Britons call such a line a queue and will talk about "queuing up". Because items leave in the same order they arrive, queues are *first in, first out* (FIFO).

The operations are:

- `dequeue` (pronounced DQ) removes and returns the front item from the queue
- `enqueue` (pronounced NQ) adds an item to the back of the queue
- `isEmpty` returns true if the queue is empty

Here is the interface:

```java
public interface Queue<T> {

    public T dequeue();

    public void enqueue(T item);
    
    public boolean isEmpty();

}
```

## Array-Based Implementation

The array-based implementation is similar to the array-implementation of a stack, with the front of the queue at index 0, but there are complications.

Enqueuing works just like pushing at first. To dequeue, you need to return the item at index 0, but then what? You could shift everything over (and decrement `size`) so that that the queue begins at index 0, but that would take linear time. A better solution is to maintain two ints, `front` and `back`. The front item is at index `front` and the next available index is `back`.

This approach causes another problem: after a series of enqueue and dequeue operations, the queue will march down the array, so the indices close to 0 are unused but unavailable. To avoid wasting space, the queue is made to wrap around to the beginning. This is done using the `%` (remainder) operator.

The last detail is that a full queue (requiring copying everything into a larger array) and an empty queue look exactly the same: `front == back`. The solution is to store at most `n - 1` items in an array of length n.

Here is the code:

```java
public class ArrayQueue<T> implements Queue<T> {

    private T[] data;

    private int front;

    private int back;

    public ArrayQueue() {
        data = (T[]) new Object[1];
    }

    @Override
    public T dequeue() {
        T result = data[front];
        front = (front + 1) % data.length;
        return result;
    }

    @Override
    public void enqueue(T item) {
        if ((back + 1) % data.length == front) { // Array is full; resize
            T[] d = (T[]) new Object[data.length * 2];
            for (int i = 0; i < data.length - 1; i++) {
                d[i] = data[(front + i) % data.length];
            }
            data = d;
        }
        data[back] = item;
        back = (back + 1) % data.length;
    }

    @Override
    public boolean isEmpty() {
        return front == back;
    }

}
```

The amortized running time for all of the queue operations is constant.

## Linked Implementation

The linked implementation is similar to the linked implementation of a stack, with the first node at the front.

Dequeuing is like popping.

Enqueuing involves adding a new successor to the *last* node in the chain. Normally finding this node requires walking down the chain, which would take linear time. A better solution is to maintain a second reference to the last node.

Here is the code:

```java
public class LinkedQueue<T> implements Queue<T> {

    private class Node {

        T item;

        Node next;

        Node(T item) {
            this.item = item;
        }

    }

    private Node front;

    private Node back;

    @Override
    public T dequeue() {
        T result = front.item;
        front = front.next;
        return result;
    }

    @Override
    public void enqueue(T item) {
        if (front == null) {
            front = new Node(item);
            back = front;
        } else {
            back.next = new Node(item);
            back = back.next;
        }
    }

    @Override
    public boolean isEmpty() {
        return front == null;
    }

    public static void main(String[] args) {
        Queue<Integer> q = new LinkedQueue<>();
        q.enqueue(1);
        q.enqueue(2);
        q.enqueue(3);
        while (!q.isEmpty()) {
            StdOut.println(q.dequeue());
        }
    }

}
```

All operations take constant time.

## Additional Resources

- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 4.3](https://introcs.cs.princeton.edu/java/43stack/)
- Cormen *et al.*, *Introduction to Algorithms, 3rd Edition*, Section 10.1

## Questions
1. :star::star: Here is an array-based queue:

    ![q is an array-based queue. The data array contains 5, 2, 7, and an unused cell. Front is 0 and back is 3.](array_queue_example.svg)
    
    Draw the final state of the queue after executing the following sequence of operations:
    ```java
    q.enqueue(4);
    q.dequeue();
    q.dequeue();
    q.enqueue(8);
    ```
## Answers
1. &nbsp;

    ![q is an array-based queue. The data array contains 8, an unused cell, 7, and 4. Front is 2 and back is 1.](array_queue_after.svg)
    
