# Operators
## Overview
*Operators* are used to combine expressions (such as [literals](data_structures/primitive_types.md#Literals)) into larger expressions. For example, in `2 + 3`, the `+` operator combines the two operands `2` and `3` into a larger expression with the value 5.

*Binary operators*, like `+`, are *infix*, meaning that they appear between their two operands. *Unary operators*, like `-` when it is used for negation rather than subtraction, are *prefix* if they appear before the operand and *postfix* if they appear afterward. There is one *ternary operator*, `?:`, which takes three arguments, one before the `?`, one between the `?` and `:`, and one after the `:`.

The operators are summarized in the table below. See the additional resources for more information.

Category|Operators|Notes
-|-|-
Arithmetic|`+ - * / %`|`%` is the remainder operator, sometimes called the modulus operator.<br>`-` can be used for negation (prefix) or subtraction(infix).
Comparison|`< <= == >= > !=`|These have boolean values.<br>`!=` means "is not equal to".
Assignment|`= ++ -- += -= *= /= %= <<= >>= &= ^= \|=`|Assignments are also statements.<br>`++` and `--` can be prefix or postfix.<br>`x++` roughly means `x = x + 1`.<br>`x += 5` roughly means `x = x + 5`.
Logical|`&& \|\| !`|These take boolean operands and produce boolean values.<br>`&&` and `\|\|` are short-circuited.<br>`!` is prefix.
Bitwise|`& \| ~ ^ << >> >>>`|These operate on integer types.<br>`~` and `^` are prefix.
Conditional|`?:`|`a ? b : c` has the value of `b` if `a` is true, `c` otherwise.

## Additional Resources
### Online
### Print
## Questions
## Answers
