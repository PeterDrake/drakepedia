# Instance Methods
## Overview
(include getters and setters)
## Additional Resources
## Questions
1. :star: Add a method `perimeter`, which takes no arguments and returns the Square's perimeter, to the class below.
    ```java
    public class Square {

        private double side;

        public Square(double s) {
            side = s;
        }

    }
    ```
1. :star: Supply the missing line in the class below.
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
1. :star: Why does the class below not compile?
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
1. :star: In another class, I have created `p`, an instance of class `Person`. When I try to print `p.height`, Java tells me that I don't have access to the private instance variable `height`. What is the proper object-oriented way to to get the value of this variable?
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
