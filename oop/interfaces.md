# Interfaces
## Overview

An *interface* is similar to a class, but it doesn't commit to any particular implementation for its methods. Instead, the interface promises one or more methods, which are provided by classes that *implement* that interface.

As an example, here is a Shape interface:

```java
public interface Shape {

    public double area();

    public double perimeter();

}
```

Notice that the normal word `class` has been replacd by `interface` and that the methods don't have bodies.

The Shape interface could be implemented by various classes:

```java
public class Circle implements Shape {

    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }
    
    @Override
    public double area() {
        return Math.PI * radius * radius;
    }

    @Override
    public double perimeter() {
        return 2 * Math.PI * radius;
    }

}
```

```java
public class Rectangle implements Shape {

    private double width;

    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
    
    @Override
    public double area() {
        return width * height;
    }

    @Override
    public double perimeter() {
        return 2 * (width + height);
    }

}
```

Shape is now a type, so you can declare:

```java
Shape s;
```

You can't actually make a shape, though:

```java
s = new Shape(); // This is illegal!
```

Instead, Shape is a *polymorphic type* that can hold an instance of any class that implements shape. For example:

```java
s = new Circle(2.4);
```

If you ask for `s.area()`, Java will use the appropriate version. This is why they're called *methods*: a Circle has one method for determining its area and a Rectangle has a different method.

Such a polymorphic type can be useful if later we want to write code that works for any Shape. For example:

```java
public class Prism {

    private Shape base;

    private double height;

    public Prism(Shape base, double height) {
        this.base = base;
        this.height = height;
    }

    public double volume() {
        return base.area() * height;
    }

}
```

## Resources
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
ARRAY OF SHAPES
IS OBJECT AN INTERFACE
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
