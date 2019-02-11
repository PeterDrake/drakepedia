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
It seems natural to most students to first write code and then test it. The surprising technique of *test-driven development* turns this upside-down, writing the test *before* the code in question. This has several advantages:
- It forces us to actually write tests rather than put off doing so forever.
- It forces us to think precisely about what a method is supposed to do.
- When writing the code, repeatedly running the test will let us know when we've succeeded.
- After a test has passed, it provides a regression test that will let us know if we later break something.

The process for test-driven development is:
1. Write a test for some new feature to be added or bug to be corrected.
1. Fail the test. If the test passes before you've written the main code or fixed the bug, there's probably something wrong with the test.
1. Write the code to be tested.
1. Pass the test. (If the test doesn't pass, go back and edit the code.)
## Additional Resources
### Online
### Print
## Questions
1. :star: What annotation has to appear before each test method in a JUnit test class?
1. :star: If you pass all of your unit tests, does that mean my program is correct?
1. :star::star: If a test doesn't pass, how do you know the problem isn't in the test itself?
1. :star::star: How do you test a user interface that involves detecting mouse clicks and graphics?
## Answers
1. `@Test`
1. No. Passing all of the tests is *necessary* but not *sufficient*. Certainly a program that *doesn't* pass the tests has a problem.
1. You can't be absolutely sure. Since the test is usually much simpler than the code being tested, any test failure is *probably* due to the code being tested, but sometimes there are bugs in the test. Testing mostly just gives us more confidence when tests *do* pass. This is is similar to the reasoning behind doing a math problem two different ways or [double-entry bookkeeping](https://en.wikipedia.org/wiki/Double-entry_bookkeeping_system).
1. In general, you don't. This is why it's important to separate back-end logic from user-interface code: the former can be easily tested, the latter cannot.
