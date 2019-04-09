# Instance Methods
## Overview
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
    
