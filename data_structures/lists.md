# Lists
## Abstract Data Type

A *list* is a sequence of elements. It is similar to an array, but it can be resized. The exact set of operations available varies from one library to another, but in general a list must support getting and setting items at particular indices, inserting and removing items while maintaining the order of the other items, and iterating through the list. A bare-bones interface is given below.

```java
public interface List<T> extends Iterable<T> {

    /** Adds item at index i, shifting later items to higher indices. */
    public void addAt(int i, T item);

    /** Returns the item at index i. */
    public T get(int i);

    /** Removes the item at index i, shifting later items to lower indices to close the resulting gap. */
    public void removeAt(int i);

    /** Sets the item at index i to T. */
    public void set(int i, T item);

    /** Returns the length of this List. */
    public int size();

}
```

The notation `extends Iterable<T>` is explained below.

## Array-Based Implementation

The array-based implementation is very similar to that for a [stack](stacks.md):

```java
import java.util.Iterator;

public class ArrayList<T> implements List<T> {

    private T[] data;

    private int size;

    public ArrayList() {
        data = (T[]) new Object[1];
    }

    @Override
    public void addAt(int i, T item) {
        if (size == data.length) { // Array is full; resize
            T[] d = (T[]) new Object[data.length * 2];
            for (int j = 0; j < size; j++) {
                d[j] = data[j];
            }
            data = d;
        }
        // Move later items down list
        for (int j = size; j > i; j--) {
            data[j] = data[j - 1];
        }
        // Put item in place
        data[i] = item;
        size++;
    }

    @Override
    public T get(int i) {
        return data[i];
    }

    @Override
    public void removeAt(int i) {
        for (int j = i; j < size - 1; j++) {
            data[j] = data[j + 1];
        }
        size--;
    }

    @Override
    public void set(int i, T item) {
        data[i] = item;
    }

    @Override
    public int size() {
        return size;
    }

    // Code to support iteration is given later

}

```

The `addAt` and `removeAt` methods take linear time in the worst case. In the best case, when the item being added or removed is at the back end of the list, they take constant amortized time.

## Linked Implementation

The linked implementation is also similar to the corresponding stack implementation:

```java
public class LinkedList<T> implements List<T> {

    private class Node {

        T item;

        Node next;

        public Node(T item, Node n) {
            this.item = item;
            next = n;
        }

    }

    private Node front;

    @Override
    public void addAt(int i, T item) {
        if (i == 0) {
            front = new Node(item, front);
        } else {
            Node n;
            for (n = front; i > 1; i--) {
                n = n.next;
            }
            n.next = new Node(item, n.next);
        }
    }

    @Override
    public T get(int i) {
        Node n;
        for (n = front ; i > 0; i--) {
            n = n.next;
        }
        return n.item;
    }

    @Override
    public void removeAt(int i) {
        if (i == 0) {
            front = front.next;
        } else {
            Node n;
            for (n = front ; i > 1; i--) {
                n = n.next;
            }
            n.next = n.next.next;
        }
    }

    @Override
    public void set(int i, T item) {
        Node n;
        for (n = front ; i > 0; i--) {
            n = n.next;
        }
        n.item = item;
    }

    @Override
    public int size() {
        int result = 0;
        for (Node n = front; n != null; n = n.next) {
            result++;
        }
        return result;
    }
    
    // Code to support iteration is given later

}

```

Again, `addAt` and `removeAt` take linear time in the worst case and constant time in the best case, but here the best case is adding or removing something from the *front* of the list. `get`, `set`, and `size` now also take linear time in the worst case because they must walk down the list to find the item in question.

## Iterables

The List interface extends the Iterable interface. This means that List makes all of the promises of Iterable and adds its own. Any class implementing List must also implement Iterable.

Because lists are iterable, you can use a [for each loop](../control_structures/loops.md#for-each-loops) to iterate through a list:

```java
for (Integer n : numbers) { // Where numbers is of type List<Integer>
    StdOut.println(n);
}
```

The Iterator interface has only one method, `iterator`. Its job is to return an Iterator object. Iterator is another interfaces that has two methods, `hasNext` ("Do you have another item?") and `next` ("Give me the next item."). To understand these, it is helpful to know that the code above is equivalent to:

```java
Iterator<Integer> iter = numbers.iterator():
while (iter.hasNext()) {
    Integer n = iter.next();
    StdOut.println(n);
}
```

This can be read as:

1. Ask `numbers` for its iterator and call it `iter`.
1. Keep asking `iter` if it has a next item. Each time it says yes, get that item, call it `n`, and print it.

To support this behavior, an implementation of Iterable (and therefore of List) must provide `iterator`. Here it is for ArrayList:

```java
@Override
public Iterator<T> iterator() {
    return new ArrayListIterator();
}
```

What is an ArrayListIterator? That is another class that is only used here. So that it can access the instance variables of the ArrayList, it is easiest to define this class *inside* the ArrayList class:

```java
private class ArrayListIterator implements Iterator<T> {

    int current;

    @Override
    public boolean hasNext() {
        return current < size;
    }

    @Override
    public T next() {
        T result = data[current];
        current++;
        return result;
    }

}
```

[Surprisingly](https://stackoverflow.com/questions/6906215/why-are-iterablee-and-iteratore-in-different-packages), the Iterator interface is in the java.util package, so the following line must appear before the definition of ArrayList:

```java
import java.util.Iterator;
```

The Iterable implementation for LinkedList is similar:

```java
@Override
public Iterator<T> iterator() {
    return new LinkedListIterator();
}

private class LinkedListIterator implements Iterator<T> {

    Node current;

    public LinkedListIterator() {
        current = front;
    }

    @Override
    public boolean hasNext() {
        return current != null;
    }

    @Override
    public T next() {
        T result = current.item;
        current = current.next;
        return result;
    }

}
```

## Resources

- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 4.3](https://introcs.cs.princeton.edu/java/43stack/)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 9.1.3

## Questions

1. :star: Of the following operations, which take linear time in the worst case for an array-based list? `addAt`, `get`, `removeAt`, `set`, `size`.
1. :star: Of the following operations, which take linear time in the worst case for a linked list? `addAt`, `get`, `removeAt`, `set`, `size`.
1. :star: Describe a situation where a LinkedList is faster than an ArrayList.
1. :star::star: Suppose `nums` is a `List<Integer>`. A programmer who is unaware of the `size` method tries to count the number of items in `nums` with the following code:
    ```java
    Iterator<Integer> iter = nums.iterator();
    int count = 0;
    while (iter.hasNext()) {
        count++;
    }
    StdOut.println(count);
    ```
    It goes into an infinite loop. Why?
## Answers
1. `addAt` and `removeAt`.
1. All of them.
1. Adding or removing the first item of a list takes constant time with a LinkedList but linear time with an ArrayList.
1. `hasNext`, unlike `next`, does not advance the iterator down the list; it merely reports the current state of the iterator. This could be fixed by adding `iter.next();` inside the while loop.
