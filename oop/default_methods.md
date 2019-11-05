# Default Methods
## Overview
In addition to [the default constructor](https://github.com/PeterDrake/drakepedia/blob/master/oop/constructors.md#the-default-constructor), every class gets a few *default methods*. These are inherited from the [Object class](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Object.html). The default versions are almost never what you want, so you'll want to override them with new definitions. Built-in classes like Integer, String, and ArrayList have sensible versions of these methods.

### `toString`
The `toString` method returns a String that represents this object in a human-readable way. What that means varies from one class to another. For a typical Point class with instance variables `x` and `y`, the `toString` method might be defined like this:

```java
public String toString() {
    return "<" + x + ", " + y + ">";
}
```

Now `new Point(3, 4).toString()` has the value `"<3, 4>"`.

In some common situations where a String is expected, such as contatenating Strings with `+` or calling `println`, if a non-String object is supplied, its `toString` method is called automatically. This means that, instead of

```java
System.out.println(p.toString());
```

you can simply say:

```java
System.out.println(p);
```

### `equals`
`a.equals(b)` should return true if `a` and `b` are equal in the sense of having the same values for their instance variables. This must be defined for each class because testing the equality of complicated instance variables (such as arrays) can be tricky. Also, some classes may ignore some instance variables; for example, a Car class might define `equals` to consider `make`, `model`, and `year` but not `miles`.

There's a surprising amount going on in a proper `equals` method, so it's usually best to let the IDE generate the method. Here's the one that IntelliJ generates for the Point class:

```java
public boolean equals(Object o) {
    if (this == o) return true;
    if (o == null || getClass() != o.getClass()) return false;
    Point point = (Point) o;
    return x == point.x &&
            y == point.y;
}
```

First notice that the type of the parameter is `Object`. This is neccessary because you are *overriding* the default method so your version has to have the same signature. If you were to make the paramater type `Point`, you would merely be *overloading* the method and the default method, which would still exist. This could lead to surprising bugs.

The first line inside the method checks to see if `this` and the parameter `o` are the same object. If they are `==`, they *must* be `equals`, so you can return `true` immediately. This line is not strictly necessary, but it saves some computation for this common case.

The next line checks for two conditions that would allow you to immediately return `false`. Since `this` can never by null, if `o` is null then they can be `equals`. Also, if `this` and `o` are not instances of the same class, they cannot be `equals`.

Having established that `o` is a Point (even though it is stored in a parameter of type Object), you know cast it to a Point and store that in a local variable called `point`.

Finally, you can actually compare the instance variables.

The default version of `equals` behaves like `==`: `a.equals(b)` only returns true if `a` and `b` are the same object.

### `@Override`
It is good style, though not required, to add `@Override` before your definition of any method you are overriding. This allows the compiler to catch certain bugs. For example, if you accidentally called your method `tostring` instead of `toString`, the compiler would give you the error message "Method does not override method from its superclass.".

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, [Section 3.3](https://introcs.cs.princeton.edu/java/33design/)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 5.2
- [API for the Object class](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Object.html)

## Questions
1. :star: Name a default method.
1. :star::star: What does the default version of `toString` do?
1. :star::star: Why provide a `toString` method instead of a `print` method?
1. :star::star: Isn't it bad style in the generated `equals` method to have a variable named `o` and omit the curly braces in the if statements?
1. :star::star: Would this work an an `equals` method for any class?
    ```java
    @Override
    public boolean equals(Object obj) {
        return this.toString().equals(obj.toString());
    }
    ```
1. :star::star::star: When you ask your IDE to generate `equals`, it also want to generate a method called `hashCode`. What's up with that?
1. :star::star::star: Suppose you define the `equals` method for Point like this:
    ```java
    public boolean equals(Point that) {
        StdOut.println("mine");
        if (that == null) {
            return false;
        }
        return x == that.x && y == that.y;
    }
    ```
    Now you define:
    ```java
    Point a = new Point(1, 2);
    Object b = new Point(1, 2);
    Point c = new Point(1, 2);
    ```
    What is `a.equals(b)`? What is `a.equals(c)`? What is `b.equals(c)`?
## Answers
1. `equals`, `toString`.
1. For the Point class, it returns something like `Point@49e4cb85`, which is the name of the class, `@`, and a representation of the object's original location in memory. This is rarely useful.
1. You might want to do something with the String other than printing it, such as writing it to a file or (in a test) comparing it to another String.
1. I think so.
1. No. This would throw a NullPointerExceptoin if `obj` was null. It might also return true in some situations where `this` and `obj` are instances of different classes. Finally, for some objects containing very large data structures, it might either give incorrect answers or be woefully inefficient (depending on how `toString` is defined).
1. `hashCode` is used by a data structure called a hash table. That data structure depends on the behavior of `equals` and `hashCode` to be similar in certain ways, so if you override one you should override the other. Until you start using hash tables you can ignore this extra method.
1. `false`, `true`, and `false` respectively. This suprising behavior depends on the fact that Object is a *polymorphic type*, which can hold an instance of any class. The type of the variable need not match the type of the object to which it refers. Specifically, `b` is of type Object, but refers to an instance of `Point`. When deciding which version of an overloaded method to use, Java generally looks at variable types, except where there is overriding. Here:
    - In `a.equals(b)`, Java sees that `a`, a Point, has one version of `equals` that takes an Object and another that takes a Point. Since the variable type of `b` is Object, the default version of `equals` is used.
    - In `a.equals(c)`, Java uses your version since the variable type of `c` is Point.
    - In `b.equals(c)`, Java sees that `b`, an Object, has only the default version of `equals`, which it uses.
    To avoid this very confusing result, make sure your `equals` method takes an Object.
