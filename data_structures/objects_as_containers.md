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

## Resources
## Questions
1. :star: What reserved word is used when creating an object?
1. :star::star: What is printed by the program below?
    ```java
    public class Mystery {

        private int x;

        public static void main(String[] args) {
            Mystery m = new Mystery();
            System.out.println(m.x);
        }

    }
    ```
QUESTION TO ADD: Trying to access instance variable from a class, e.g., Mystery.x above.
## Answers
1. `new`
1. 0, which is the default value of `x`.
