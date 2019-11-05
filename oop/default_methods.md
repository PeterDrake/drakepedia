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

Now `new Point(3, 4).toString()` has the value `"<3, 4">`.

In some common situations where a String is expected, such as contatenating Strings with `+` or calling `println`, if a non-String object is supplied, its `toString` method is called automatically. This means that, instead of

```java
System.out.prilntln(p.toString());
```

you can simply say:

```java
System.out.prilntln(p);
```

### `equals`
`a.equals(b)` should return true if `a` and `b` are equal in the sense of having the same values for their instance variables. This must be defined for each class because testing the equality of complicated instance variables (e.g., arrays) can be tricky. Also, some classes may ignore some instance variables; for example, a Car class might define `equals` to consider `make`, `model`, and `year` but not `miles`.

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

The next line checks for two conditions that would allow you to immediately return `false`. Since `this` can never by null, if `o` is null then they can be `equals`. Also, if `this` and `o` are not instance of the same class, they cannot be `equals`.

Having established that `o` is a Point (even though it is stored in a parameter of type Object), you know cast it to a Point and store that in a local variable called `point`.

Finally, you can actually compare the instance variables.

### `@Override`
It is good style, though not required, to add `@Override` before your definition of any method you are overriding. This allows the compiler to catch certain bugs. For example, if you accidentally called your method `tostring` instead of `toString`, the compiler would give you the error message "Method does not override method from its superclass.".

## Resources
- [API for the Object class](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Object.html)

## Questions
1. :star: Name a default method.
DEFAULT VERSION OF TOSTRING
BAD STYLE IN GENERATE EQUALS
EQUALS BY COMPARING TOSTRING RESULTS
EQUALS TRICKINESS WITH WRONG ARG TYPE
## Answers
1. `equals`, `toString`.
