# Inanimate Objects
## Overview
[Arrays](arrays.md) allow you to combine multiple values into a single object in memory. They have two limitations:

- The elements are only identified by numeric indices. This makes it difficult to remember which is which.
- The elements all have to be of the same type.

You can avoid both of these limitations by defining a new *class* of objects:
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

Now that you have a Car, you can access its elements, called *instance variables* or *fields*, by name:
```java
c.year = 1978;
```

If you create another Car
```java
Car d = new Car();
```
then each instance of the class has its own version of each instance variable. In other words, `c.model` and `d.model` are different boxes.

Instance variables are automatically initialized to default values: 0 for numeric types, `false` for booleans, and `null` for reference types.
## Resources
This page is intended as a very gentle introduction to objects; for simplicity, the objects here don't do anything but hold data (hence "inanimate"). There is much more to learn, covered in other sections of the [Drakepedia](../README.md). Other books and websites tend to dive in much more quickly, getting straight to constructors, instance methods, and so on. It is perhaps best to hold off on such topics until you have some practices using inanimate objects.
## Questions
1. :star: What reserved word is used when creating an object?
1. :star::star: If you define a class Tree, can you make an array of Trees?
1. :star::star: Can a class be used as the type of an instance variable in another class?
1. :star::star: Can an object be passed as an argument to a method?
1. :star::star: Can an object be returned from a method?
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
1. Yes. It's even possible (and sometimes useful) to use a class as the type of an instance variable in the *same* class.
1. Yes. In fact, the ability to pass in one object rather than several separate arguments is one of the main reasons for defining classes of objects.
1. Yes. Since a method can only return one value, returning an object is one of the best ways for a method to return complex information.
1. 0, which is the default value of `x`.
1. The program does not compile. You have to ask for the value of `x` for a particular Point. Otherwise, since there may be many Points, Java doesn't know which one to look in for an `x` value.
