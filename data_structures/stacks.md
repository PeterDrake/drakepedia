# Stacks

## Abstract Data Type

An *abstract data type* defines a data type and the associated operations. It does not say anything about how these operations are implemented; it merely conveys the idea of the data type.

The *stack* abstract data type defines a stack as a sequence of items, with the following operations:

-`push` adds an item to the top of the stack
-`pop` removes and returns the top item from the stack
-`isEmpty` returns true if the stack is empty

The standard metaphor for a stack is one of those spring-loaded stacks of plates you might find in a cafeteria. You can push a new plate onto the stack or pop one off the top, but there's no way to access the plates underneath. Stacks are said to be *last in, first out* (LIFO).

in Java, an abstract data type is represented by an [interface](../oop/interfaces.md).

## Array-Based Implementation
## Linked Implementation
## Additional Resources
## Questions
1. :star::star: Here is a linked stack:

    ![s is a linked stack containing, from top to bottom, 5, 2, 7](linked_stack_example.svg)
    
    Draw the final state of the stack after executing the following sequence of operations:
    ```java
    s.push(4);
    s.pop();
    s.pop();
    s.push(8);
    ```
## Answers
1.
    ![s is a linked stack containing, from top to bottom, 8, 2, 7](linked_stack_after.svg)
    
