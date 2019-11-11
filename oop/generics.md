# Generics
## Overview
In order to reuse classes, you would like them to be as general-purpose as possible. The requirement to specify types can make this difficult: a class meant to hold two ints won't work in a situation where two doubles or two Strings are needed. Java's solution is to allow *generic types*, which allow the types of components to be specified later.

### Using Generic Types
The built-in type ArrayList, in the java.util package, is generic. When you declare a variable of type ArrayList, you have to specify the type of the elements in the list:

```java
ArrayList<String> words;
```

Similarly, when you create an instance of ArrayList, you again specify the element type:

```java
words = new ArrayList<String>();
```

Now the ArrayList will behave appropriately: `add` takes a String, `get` returns a String, and so on.

### Implementing Generic Types

Here is a definition of a class that can hold two values of any one type:

```java
public class Pair<T> {
    
    private T a;
    
    private T b;

    public Pair(T a, T b) {
        this.a = a;
        this.b = b;
    }

    public T getA() {
        return a;
    }

    public void setA(T a) {
        this.a = a;
    }

    public T getB() {
        return b;
    }

    public void setB(T b) {
        this.b = b;
    }
    
}
```

`T` is a *type parameter*. Just like a normal variable can represent any value, a type parameter can represent any reference type. That type is determined at the time that someone declares a variable or creates an object of type pair:

```java
Pair p = new Pair<Integer>(3, 4);
```

Throughout the class, `T` stands for the specified type.

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 4.3](https://introcs.cs.princeton.edu/java/43stack/)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Chapter 8

## Questions
CAN'T USE PRIMITIVES FOR TYPE PARAMS
CAN INTERFACES BE GENERIC
TYPE PARAM NAMES
WHAT ABOUT JUST USING OBJECT
DIAMOND NOTATION
PLAYING WITH ARRAYS
## Answers
By convention, type parameter names start with upper-case letters (and are often single letters).
