# Interfaces
## Overview
## Additional Resources
## Questions
1. :star: What is an interface?
1. :star: What is special about methods that appear in interfaces?
1. :star::star: Define two classes `Add` and `Multiply` that implement the interface below. If, for example, `m` is an instance of `Multiply`, then `m.apply(3, 4)` should return 12.
    ```java
    public interface Operator {

        /** Returns the result of applying this operator to a and b. */
        public double apply(double a, double b);

    }
    ```
## Answers
1. An interface defines a type but doesn't specify how it is implemented. It can be thought of as a promise or contract, indicating one or more methods that must be supplied by any class implementing that interface.
1. They don't have bodies, just the first line (method signature).
1.
    ```java
    public class Add implements Operator {

        @Override
        public double apply(double a, double b) {
            return a + b;
        }

    }
    ```
    ```java
    public class Multiply implements Operator {

        @Override
        public double apply(double a, double b) {
            return a * b;
        }

    }
    ```
