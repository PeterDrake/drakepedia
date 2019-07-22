# Objects as Containers
## Overview
[Arrays](arrays.md) allow you to combine multiple values into a single object. They have two limitations:

- The elements are only identified by numeric indices. This makes it difficult to remember which is which.
- The elements all have to be of the same type.

You can avoid both of these limitations by defining a new *class*:
```java
class Car {
    String make;
    String model;
    int year;
    int miles;
}
```
This code would appear in its own file, `Car.java`.

To create an object that is an *instance* of this class:
```java
Car c = new Car();
```
Note that `Car` is now a valid type.

Now that we have a Car, we can access its elements, called *instance variables*, by name:
```java
c.year = 1978;
```

If we create another Car
```java
Car d = new Car();
```
then each one has its own version of each instance variable. In other words, `c.model` and `d.model` are different boxes.

Instance variables are automatically initialized to default values: 0 for numeric types, `false` for booleans, and `null` for reference types.
## Resources
## Questions
1. :star: What reserved word is used when creating an object?
1. :star::star: If you define a class Tree, can you make an array of Trees?
1. :star::star: If you define the class
    ```java
    class Point {
        double x;
        double y;
    }
    ```
    what is printed by the code below?
    ```java
    Point p = new Point();
    System.out.println(p.x);
    ```
1. :star::star::star: Given the definition of `Point` above, what happens if you ask for `Point.x`?
## Answers
1. `new`
1. Yes. Simply declare a variable of type `Tree[]`.
1. 0, which is the default value of `x`.
1. The program does not compile. You have to ask for the value of `x` for a particlar Point. Otherwise, since there may be many Points, Java doesn't know which one to look in for an `x` value.
