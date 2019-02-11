# Testing
## Types of Testing
Testing is how we know whether our software is working correctly, that is, doing what it's supposed to do. There are several kinds of testing:
- *System testing* runs the entire program. This is probably what you did in your first programming class. For large programs, system testing is necessary but not sufficient. A system test is likely to leave some parts of the program insufficiently tested. Even if a bug is discovered, it will be very difficult to tell where in the code the defect lies.
- *Unit testing* tests individual parts of the program (e.g., methods). Unit testing has two big advantages over system testing. First, it can happen a lot earlier, before the entire system has been built. This is important because it gives you a chance to fix one bug before introducing the next one. Second, if a bug is found, unit testing gives a strong indication of where it is.
- *Regression testing* re-tests the system (or units thereof) after making a change to the program, to ensure that nothing broke.
## JUnit
Manual testing is fine for very small, simple programs but it quickly becomes tedious and error-prone for larger ones. When you hear "tedious and error-prone", you should think, "Can I automate this?" JUnit is a tool for automating unit tests in Java. (Other languages have similar frameworks.)

A JUnit test suite is a class containing test methods. JUnit allows you to run all of the tests in a class (or even in a directory) at the click of a button.

Each method is annotated with `@Test` before the method signature. A test generally sets up some data structures and then makes an assertion about the result of some method call:
```java
assertEquals(10, sumOfFirstNNumbers(4));
```
where `sumOfFirstNNumbers` is the method being tested. In this case, `10` is the expected value and `sumOfFirstNNumbers(4)` is the computation that is supposed to return that result.
## Test-Driven Development

## Additional Resources
### Online
### Print
## Questions
1. :star: What annotation has to appear before each test method in a JUnit test class?
## Answers
1. `@Test`
