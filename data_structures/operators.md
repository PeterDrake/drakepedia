# Operators
## Overview
*Operators* are used to combine expressions (such as [literals](data_structures/primitive_types.md#Literals)) into larger expressions. For example, in `2 + 3`, the `+` operator combines the two operands `2` and `3` into a larger expression with the value 5.

*Binary operators*, like `+`, are *infix*, meaning that they appear between their two operands. *Unary operators*, like `-` when it is used for negation rather than subtraction, are *prefix* if they appear before the operand and *postfix* if they appear afterward. There is one *ternary operator*, `?:`, which takes three arguments, one before the `?`, one between the `?` and `:`, and one after the `:`.

The operators are summarized in the table below. See the additional resources for more information.

Category|Operators|Notes
-|-|-
Arithmetic|`+ - * / %`|`%` is the remainder operator, sometimes called the modulo operator.<br>`-` can be used for negation (prefix) or subtraction (infix).
Comparison|`< <= == >= > !=`|These have boolean values.<br>`!=` means "is not equal to".
Assignment|`= ++ -- += -= *= /= %= <<= >>= &= ^= \|=`|Assignments are also statements.<br>`++` and `--` can be prefix or postfix.<br>`x++` roughly means `x = x + 1`.<br>`x += 5` roughly means `x = x + 5`.
Logical|`&& \|\| !`|These take boolean operands and produce boolean values.<br>`&&` and `\|\|` are short-circuited.<br>`!` is prefix.
Bitwise|`& \| ~ ^ << >> >>>`|These operate on integer types.<br>`~` and `^` are prefix.
Conditional|`?:`|`a ? b : c` has the value of `b` if `a` is true, `c` otherwise.

## Additional Resources
### Online
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Section 1.2](https://introcs.cs.princeton.edu/java/12types/)
- Sedgewick and Wayne, *Introduction to Programming in Java* booksite, [Appendix A: Operator Precedence in Java](https://introcs.cs.princeton.edu/java/11precedence/)
- Anderson, [Bit Twiddling Hacks](https://graphics.stanford.edu/~seander/bithacks.html) (These are in C, but the operators are pretty much the same in C and in Java.)
### Print
- Sedgewick and Wayne, *Introduction to Programming in Java*, Section 1.2
- Horstmann, *Core Java, Volume I: Fundamentals, 11th Edition*, Section 3.5
## Questions
1. :star: What is the value of `2 + 3 * 4`?
1. :star: What is the value of `83 % 10`?
1. :star::star::star: What are the values of the variables after the following code is evaluated?
    ```java
    int a = 1;
    int b = a++;
    int c = ++a;
    ```
1. :star::star::star: What is the difference between `>>` and `>>>`?
1. :star::star::star: What is the value of `-32 % 10`?
1. :star::star::star: If `a` and `b` are boolean expressions, what is the difference between `a && b` and `a & b`?
## Answers
1. 14, because multiplication has higher operator precedence than addition. It is not reasonable to memorize the entire operator precedence hierarchy; whenever there is any doubt, use parentheses.
1. 3, because when 83 is divided by 10 the remainder is 3.
1. `a` is 3, `b` is 1, and `c` is 3. This is because `++a` increments `a` *before* yielding a value, but `a++` increments `a` *after* yielding a value.
1. The difference lies in what is shifted in on the left side. `>>` copies the leftmost (sign) bit, so that `a >> 3` is `a` divided by 2 to the 3rd power. `>>>` shifts in a 0, which is sometimes preferable when an int is being interpreted as a set of bits rather than as a number.
1. -2. If the first argument to `%` is negative, the result is negative as well. This is consistent with the interpretation of `%` as "remainder" but not really with the interpretation as "modulo".
1. `a && b` is short-circuited: if `a` is false, `b` is not evaluated (which might matter if `b` is actually a method call). `a & b` is not short-circuited.
