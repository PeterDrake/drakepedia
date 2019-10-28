# Access Modifiers
## Overview
In government, it is good to make everything (meeting minutes, spending, etc.) as widely visible as possible to prevent corruption. Surprisingly, the opposite is true in software development. A class should reveal no more than necessary about its inner workings. This is true for three reasons:

* People using your class should not have to think about how it works. Since the primary problem in software development is that there is far too much going on for anyone to keep track of, it is crucial to be able to treat methods, classes, and so on as black boxes, concentrating on their input and output and not on how they work.
* Someone who only partially understands your class might put your instance variables into an invalid state. For example, they might accidentally set the mass of a Particle to a negative value.
* If someone knows how your class works, there is a danger that they will write code that depends on your class working that way. This means that any changes you make could break *their* code. Strict encapsulation prevents this problem.

To support *information hiding*, Java provides four *access modifiers*, which can be used before any instance variable or method:

| Access Modifier | Visibility |
| --- | --- |
| `private` | This class only |
| (package private) | This package only |
| `protected` | This package and descendents of this class |
| `public` | All classes |

There is no keyword for the package private level; this is the default that you get if you don't specify one of the others.

In very large prorgrams it is useful to group classes into packages. I don't bother with this in CS2. I just put everything in the nameless default package, so the last three levels are equivalent there.

### Rules for Using Access Modifiers

Before introducing access modifiers, I ask students to follow a simple rule:

* The `main` method has to be public. Leave everything else package private.

After introducing them, I broaden the rules:

* Instance variables should be private.
* Methods should be public.

The full rule, for sophisticated Java programmers using packages, is:

* Make everything as private as possible.

For example, a "helper method" that is used only to support another public method might reasonably be private. If, however, that method is also going to be called by a unit test, it will have to be package private.

## Getters and Setters

Suppose we have a Person class with an instance variable `height`. The rules above suggest that `height` should be private:

```java
/** Height in inches. */
private int height; 
```

This is correct, but what if you need to get the height of person `p` in another class? The compiler won't let you refer to `p.height` because it is private.

The correct solution is to provide a *getter* (*accessor*) and a *setter* (*mutator*):

```java
public int getHeight() {
    return height;
}

public void setHeight(int height) {
    this.height = height;
}
```

Now other classses can refer to, for example, `p.getHeight()`.

If other classes can now modify `height` using `setHeight`, what was the point of all this? Why not just make `height` public? Using getters and setters provides several advantages:

* If you want to make it so that others can see an instance variable but not modify it, you can provide a getter but no setter.
* You can change your internal representation without modifying the getter and setter behavior. For example, a class representing a two-dimensional vector might use rectangular or polar coordinates; someone using such a class doesn't have to know which it is and their code won't break if the representation is changed.
* A setter can enforce constraints, such as disallowing negative heights or making sure that multiple instance variables have consistent values.
* While debugging, you know that any change to the instance variable *must* either be in thie class or go through the setter, so you only have to look at code in this class.

Most IDEs can automatically generate getters and setters.

## Resources
- Sedgewick and Wayne, *Introduction to Programming in Java*, Sections [3.2](https://introcs.cs.princeton.edu/java/32class/) and [3.3](https://introcs.cs.princeton.edu/java/33design/)
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Chapters 4-5

## Questions
1. :star: In another class, I have created `p`, an instance of class `Person`. When I try to print `p.height`, Java tells me that I don't have access to the private instance variable `height`. What is the proper object-oriented way to to get the value of this variable?
1. :star::star: If I want to set an instance variable of another object of the same class, do I have to use a setter?
1. :star::star: Suppose I have an object `airplane` that has an instance variable `speed`. How can I increase `speed` by 3.2 from another class? Because `speed` is private, I can't just say `airplane.speed += 3.2;`.
1. :star::star: If I have a boolean instance variable `onFire`, what is the associated getter called?
## Answers
1. `p.getHeight()`.
1. No; code in the same class can access private parts of any instance of the class. You might choose to use a setter if does extra work, like enforcing constraints.
1. `airplane.setSpeed(plane.getSpeed() + 3.2);`
1. `isOnFire`. This convention is used for booleans so that expressions like `hair.isOnFire()` will make grammatical sense in English.
