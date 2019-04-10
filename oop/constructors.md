# Constructors
## Overview
## Additional Resources
## Questions
1. :star: Where should an instance variable be initialized?
1. :star: Describe a situation where it's necessary to use `this`.
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
1. The constructor does not initialize `x`; it creates a new local variable with the same name.
