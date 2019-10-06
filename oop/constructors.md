# Constructors
## Overview
Suppose you define:

```java
class Point {
    double x;
    double y;
}
```

Every time you create an instance of Point, you have to initialize the instance variables:

```java
Point p = new Point();
p.x = 3;
p.y = 5;
```

It would be more convenient if you could specify these values on the line where you created the object:

```java
Point p = new Point(3, 5);
```

You can, in fact, do this if the definition of Point includes an appropriate *constructor*:

```java
class Point {
    
    double x;
    
    double y;
    
    Point(double initialX, double initialY) {
        x = initialX;
        y = initialY;
    }

}
```

The constructor looks much like a static method, but:

- It is not declared `static`,
- It has no return type, and
- It has exactly the same name as the class (starting with an upper-case letter).

Every time you use `new` to create an object, you are calling a constructor.

### The Default Constructor

If you do not explicitly define a constructor (as in the first definition of Point above), Java automatically provides a default constructor that takes no arguments and doesn't do anything. This is what was used in the first object creation above.

If you *do* explicitly define a constructor, you *do not* get a default constructor. When we add a constructor to the definition of Point, it is no longer legal to say `new Point()`.

### `this`

The parameter names `initialX` and `initialY` above are a bit awkward. It would be nice if you could define the constructor as:

```java
Point(double x, double x) {
    x = x;
    y = y;
}
```

Lines like

```java
x = x;
```

seem suspicious. In fact, this constructor does not work properly. The parameters are new local variables, not references to the instance variables. Inside the method `x` refers to the parameter, not the instance variable. The parameter is said to *shadow* the instance variable, because it prevents the light of the instance variable from reaching down into the depths of the method. The line

```java
x = x;
```

simply sets the parameter to its own value, which of course has no effect.

All is not lost. The instance variable can still be referred to as `this.x`, that is, the `x` instance variable of `this`, which is the object currently being created. You can therefore use the parameter names you want:

```java
Point(double x, double x) {
    this.x = x;
    this.y = y;
}
```

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 3.2](https://introcs.cs.princeton.edu/java/32class/)


## Questions
1. :star: Where should an instance variable be initialized?
1. :star: Describe a situation where it's necessary to use `this`.
1. :star::star: Can constructors be overloaded?
1. :star::star: Explain why the program below does not print `5`.
    ```java
    public class Box {

      private int x;

      public Box() {
          int x = 5;
      }

      public static void main(String[] args) {
          System.out.println(new Box().x);
      }

    }
    ```
## Answers
1. In a constructor. It is legal to initialize them where they are declared, but it's better style to do it in a constructor. If you initialize one *both* where it is declared *and* in a constructor, anyone reading your code will have to both notice this and look up which one takes precedence. It is better to be consistent. Since complicated multi-line initializations (e.g., arrays that have to be filled in with loops) can only happen in the constructor, it's best to put all initializations there.
1. When a local variable (say, `x`) shadows an instance variable, the instance variable must be referred to as `this.x`.
1. Yes. For example, the built-in String class has one constructor that takes a `char[]` and one that takes another String (and creates a copy of it).
1. The constructor does not initialize `x`; it creates a new local variable with the same name.
