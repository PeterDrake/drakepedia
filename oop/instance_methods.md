# Instance Methods
## Overview
In procedural langauges like Fortran and C, the world is made of data structures and you *do things to them*. For example, if you have a data structure `v`representing a two-dimensional vector, you might call functions like `length(v)` to determine the length of `v` or `add(v, w)` to get the sum of vectors `v` and `w`.

In object-oriented languages like C++ and Java, the world is made of objects and you *ask them to do things*. If `v` is an object (an instance of a class Vector), you would say `v.length()` to get the length of `v`. Think of this expression as asking the object, "What is your length?" Similarly, you might say `v.add(w)` to ask the object, "What is the result of adding you to `w`?"




### `this` Revisited
### Getters and Setters
## Resources
## Questions
1. :star::star: Add a method `perimeter`, which takes no arguments and returns the Square's perimeter, to the class below.
    ```java
    public class Square {

        private double side;

        public Square(double s) {
            side = s;
        }

    }
    ```
1. :star::star: Supply the missing line in the class below.
    ```java
    public class Snake {

        public Snake(double length) {
            this.length = length;
        }

        public double getLength() {
            return length;
        }

    }    
    ```
1. :star::star: Why does the class below not compile?
    ```java
    public class Account {

        private int balance;

        public int getBalance() {
            return balance;
        }

        public static void main(String[] args) {
            System.out.println(getBalance());
        }

    }
    ```
1. :star::star: In another class, I have created `p`, an instance of class `Person`. When I try to print `p.height`, Java tells me that I don't have access to the private instance variable `height`. What is the proper object-oriented way to to get the value of this variable?
TODO: Move this to the page on access levels and remove all access levels from this page.
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
1.
    ```java
    public double perimeter() {
        return 4 * side;
    }
    ```
1. The line
    ```java
    private double length;
    ```
    should be added inside the class (but not inside any method).
1. The instance method `getBalance` cannot be called from the static method `main`. It would work to print `new Account().getBalance()`.
1. `p.getHeight()`.
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
