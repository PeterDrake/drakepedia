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

There is no keywoard for the package private level; this is the default that you get if you don't specify one of the others.

In very large prorgrams it is useful to group classes into packages. I don't bother with this in CS2, putting everything in the nameless default package, so the last three levels are equivalent there.

### Rules for Using Access Modifiers

Before introducing access modifiers, I ask students to follow a simple rule:

* The `main` method has to be public. Leave everything else package private.

After introducing them, I broaden the rules:

* Instance variables should be private.
* Methods should be public.

The full rule, for sophisticated Java programmers using packages, is:

* Make everything as private as possible.

For example, a "helper method" that is used only to support another public method, might reasonably be private. If, however, that method is also going to be called by a unit test, it will have to be package private.

## Getters and Setters


### Constants

## Resources
## Questions
1. :star::star: In another class, I have created `p`, an instance of class `Person`. When I try to print `p.height`, Java tells me that I don't have access to the private instance variable `height`. What is the proper object-oriented way to to get the value of this variable?
## Answers
1. `p.getHeight()`.
