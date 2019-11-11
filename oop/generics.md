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

`T` is a *type parameter*. Just like a normal variable can represent any value, a type parameter can represent any reference type. That type is determined at the time that someone declares a variable or creates an object of type Pair:

```java
Pair p = new Pair<Integer>(3, 4);
```

Throughout the class, `T` stands for the specified type.

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 4.3](https://introcs.cs.princeton.edu/java/43stack/)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Chapter 8

## Questions
1. :star::star: The compiler complains if you try to declare a variable of type `ArrayList<int>`. How do you fix this problem?
1. :star::star: Can [interfaces](interfaces.md) be generic?
1. :star::star: What is the naming convention for type parameters?
1. :star::star::star: Since the [Object class](default_methods.md) can hold an instance of any type, why bother with generics? Why not just have ArrayList hold Objects?
1. :star::star::star: When you write
    ```java
    ArrayList<Animal> menagerie = new ArrayList<Animal>();
    ```
    your IDE may suggest removing the second appearace of `Animal`. Isn't it needed?
1. :star::star::star: If you try to define
    ```java
    public class Sequence<T> {

        private T[] data;

        public Sequence() {
            data = new T[10];
        }

    }
    ```
    Java complains: `Type parameter 'T' cannot be instantiated directly.` What's going on and how can it be fixed?
## Answers
1. Values provided for type parameters must be reference types, not primitive types. Use the corresponding [wrapper class](wrapper_classes.md): `ArrayList<Integer>`.
1. Yes. Any class interface implementing such an interface must either also be generic
    ```java
    public class Box<T> implements Container<T> { ... }
    ```
    or specify a value for the type parameter:
    ```java
    public class BoxOfInts implements Container<Integer> { ... }
    ```
1. By convention, type parameter names start with upper-case letters (and are often single letters).
1. While this would work, it would prevent the compiler from catching certain bugs. If an ArrayList defined in this way was intended to hold Strings, the compiler wouldn't know to reject attempts to `add` Integers. Also, the return type of `get` would have to be Object; the resulting value would have to be cast to some other type before using methods specific to that type.
1. No. Since you already declared the full type of `menagerie`, Java allows you avoid redundantly specifying the type parameter when you create the object:
    ```java
    ArrayList<Animal> menagerie = new ArrayList<>();
    ```
    This is sometimes called *diamond notation* because `<>` looks like a diamond shape.
1. Generics do not always play well with arrays. This is a wart in the Java language, resulting from the historical fact that generics were added later in the development of the language. The workaround is to create an array of Object, then cast it to an array of Ts:
    ```java
    data = (T[])new Object[10];
    ```
