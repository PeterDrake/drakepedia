# Instance Methods
## Overview
In procedural langauges like Fortran and C, the world is made of data structures and you *do things to them*. For example, if you have a data structure `v`representing a two-dimensional vector, you might call functions like `length(v)` to determine the length of `v` or `add(v, w)` to get the sum of vectors `v` and `w`.

In object-oriented languages like C++ and Java, the world is made of objects and you *ask them to do things*. If `v` is an object (an instance of a class Vector), you would say `v.length()` to get the length of `v`. Think of this expression as saying to the object, "Tell me your length." Similarly, you might say `v.add(w)` to say to the object, "Tell me the result of adding you to `w`."

The things that an object knows how to do are called *instance methods*, because you call them on specific instances (objects). This is constrasted with static methods, which are called on classes, as in `Math.sin(x)`.

Instance methods are defined inside a class, but they are not declared static. Here is the definition of Vector including a [constructor](constructors.md) and the methods described above:

```java
public class Vector {

    double x;

    double y;

    Vector(double x, double y) {
        this.x = x;
        this.y = y;
    }

    double length() {
        return Math.sqrt((x * x) + (y * y));
    }

    Vector add(Vector that) {
        return new Vector(x + that.x, y + that.y);
    }
    
}
```

It is worth making sure you understand the definition of `add`. The body could have been written as

```java
return new Vector(this.x + that.x, that.y + that.y);
```

to emphasize that you are adding together the value of `x` for `this` (the object on which `add` was called) and the value of `x` for `that` (the argument passed to the method). When there is no ambiguity, you are allowed to leave off `this.`.

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 3.2](https://introcs.cs.princeton.edu/java/32class/)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 4.3

## Questions
1. :star: When is an instance method declared static?
1. :star::star: Is `this` a reserved word? What about `that`?
1. :star::star: Add a method `perimeter`, which takes no arguments and returns the Square's perimeter, to the class below.
    ```java
    class Square {

        double side;

        Square(double s) {
            side = s;
        }

    }
    ```
1. :star::star: Supply the missing line in the class below.
    ```java
    class Snake {

        Snake(double length) {
            this.length = length;
        }

        double getLength() {
            return length;
        }

    }    
    ```
1. :star::star: Why does the class below not compile?
    ```java
    class Account {

        int balance;

        int getBalance() {
            return balance;
        }

        static void main(String[] args) {
            System.out.println(getBalance());
        }

    }
    ```
1. :star::star: By adding an instance variable, modify the class below so that the instance methods don't need arguments.
    ```java
    class Square {

        public static void main(String[] args) {
            Square s = new Square();
            double side = 3;
            System.out.println("Area: " + s.area(side));
            System.out.println("Perimeter: " + s.perimeter(side));
        }

        double area(double side) {
            return side * side;
        }

        double perimeter(double side) {
            return side * 4;
        }

    }
    ```
## Answers
1. Never. By definition, an instance method is one that is *not* declared static.
1. `this` is a [reserved word](https://en.wikipedia.org/wiki/List_of_Java_keywords). `that` is not, but it is sometimes a reasonable name for a parameter of the same type as `this`.
1.
    ```java
    double perimeter() {
        return 4 * side;
    }
    ```
1. The line
    ```java
    double length;
    ```
    should be added inside the class (but not inside any method).
1. The instance method `getBalance` cannot be called from the static method `main`. It would work to print `new Account().getBalance()`.

1.
    ```java
    class Square {

        double side;

        public static void main(String[] args) {
            Square s = new Square(3);
            System.out.println("Area: " + s.area());
            System.out.println("Perimeter: " + s.perimeter());
        }

        Square(double side) {
            this.side = side;
        }

        double area() {
            return side * side;
        }

        double perimeter() {
            return side * 4;
        }

    }
    ```
