# 3.1 Operators

<code-block lang="BNF" src="definitions.bnf" include-lines="23" />

An operator consists of one or multiple of the in the definitions file defined characters (with no spaces in between). The only exception are the parentheses, which hold a special use case. An operator takes one or two operands. In the first case the operand can either be on the right or the left side of the operator.

> The reason the standard is so loose in the definition what an operator is, is because later standards may define a way
> to define custom operators.

**Example**:

Following examples are considered valid operators (although the compiler/interpreter would throw an error, as they are not defined):
`+`, `++`, `+-`, `/`, `/+-!<>`

## 3.1.1 Comparing operators

Comparing operators all return an object of type [`sl.types::bool`](TBD.md). It returns `1` if the condition is true and
`0` if the condition is false.

### 3.1.1.1 The equals operator

| Operand 1 type | Operand 2 type | Result type      |
|----------------|----------------|------------------|
| `T`            | `T`            | `sl.types::bool` |

The equals operator consists of two equal signs (`==`) and compares the two operands. It returns
`1` if the operands are equal and `0` if they are not.

If the operand are equal is determined by first comparing the type of the operands and then the values of the properties of the object.

### 3.1.1.2 The not equals operator

| Operand 1 type | Operand 2 type | Result type      |
|----------------|----------------|------------------|
| `T`            | `T`            | `sl.types::bool` |

The not equals operator consists of an exclamation mark and an equal sign (
`!=`) and compares the two operands. It returns `1` if the operands are not equal and `0` if they are.

If the operand are equal is determined by first comparing the type of the operands and then the values of the properties of the object.

### 3.1.1.3 The greater than operator

| Operand 1 type     | Operand 2 type     | Result type      |
|--------------------|--------------------|------------------|
| `sl.types::number` | `sl.types::number` | `sl.types::bool` |
| `sl.types::number` | `sl.types::int`    | `sl.types::bool` |
| `sl.types::int`    | `sl.types::int`    | `sl.types::bool` |
| `sl.types::int`    | `sl.types::number` | `sl.types::bool` |

The greater than operator consists of a greater than sign (`>`) and compares the two operands. It returns
`1` if the first operand is greater than the second and `0` if it is not.

### 3.1.1.4 The greater than or equal operator

| Operand 1 type     | Operand 2 type     | Result type      |
|--------------------|--------------------|------------------|
| `sl.types::number` | `sl.types::number` | `sl.types::bool` |
| `sl.types::number` | `sl.types::int`    | `sl.types::bool` |
| `sl.types::int`    | `sl.types::int`    | `sl.types::bool` |
| `sl.types::int`    | `sl.types::number` | `sl.types::bool` |

The greater than or equal operator consists of a greater than sign and an equal sign (
`>=`) and compares the two operands. It returns `1` if the first operand is greater than or equal to the second and
`0` if it is not.

### 3.1.1.5 The less than operator

| Operand 1 type     | Operand 2 type     | Result type      |
|--------------------|--------------------|------------------|
| `sl.types::number` | `sl.types::number` | `sl.types::bool` |
| `sl.types::number` | `sl.types::int`    | `sl.types::bool` |
| `sl.types::int`    | `sl.types::int`    | `sl.types::bool` |
| `sl.types::int`    | `sl.types::number` | `sl.types::bool` |

The less than operator consists of a less than sign (`<`) and compares the two operands. It returns
`1` if the first operand is less than the second and `0` if it is not.

### 3.1.1.6 The less than or equal operator

| Operand 1 type     | Operand 2 type     | Result type      |
|--------------------|--------------------|------------------|
| `sl.types::number` | `sl.types::number` | `sl.types::bool` |
| `sl.types::number` | `sl.types::int`    | `sl.types::bool` |
| `sl.types::int`    | `sl.types::int`    | `sl.types::bool` |
| `sl.types::int`    | `sl.types::number` | `sl.types::bool` |

The less than or equal operator consists of a less than sign and an equal sign (
`<=`) and compares the two operands. It returns `1` if the first operand is less than or equal to the second and
`0` if it is not.

### 3.1.1.7 The includes operator

| Operand 1 type   | Operand 2 type       | Result type      |
|------------------|----------------------|------------------|
| `T`              | `sl.types::array<T>` | `sl.types::bool` |
| `sl.types::type` | `sl.types::type`     | `sl.types::bool` |

The includes operator consists of a pipe sign and a greater than sign (`|>`) and compares the two operands. It returns
`1` if the first operand is included in the second and
`0` if it is not. The first operand can be any type and the second operand has to be an array of the same type.

If the first operand is an object of type
`sl.types::type`, the second operand has to be from that type as well, and it returns
`1` if the first type inherits or implements the second type and `0` if it does not.

## 3.1.2 Arithmetic operators

Arithmetic operators all return an object of type [`sl.types::number`](TBD.md) or [
`sl.types::int`](TBD.md) (Except the plus operator which can also return an object of the type [
`sl.types::string`](TBD.md)). They perform arithmetic operations on the operands.

### 3.1.2.1 The plus operator

| Operand 1 type     | Operand 2 type     | Result type        |
|--------------------|--------------------|--------------------|
| `sl.types::number` | `sl.types::number` | `sl.types::number` |
| `sl.types::number` | `sl.types::int`    | `sl.types::number` |
| `sl.types::int`    | `sl.types::int`    | `sl.types::int`    |
| `sl.types::int`    | `sl.types::number` | `sl.types::number` |
| `sl.types::string` | `sl.types::string` | `sl.types::string` |

The plus operator consists of a plus sign (`+`) and adds the two operands. It returns the sum of the two operands.

If both operands are of the type [`sl.types::string`](TBD.md) it concatenates the two strings.

### 3.1.2.2 The minus operator

| Operand 1 type     | Operand 2 type     | Result type        |
|--------------------|--------------------|--------------------|
| `sl.types::number` | `sl.types::number` | `sl.types::number` |
| `sl.types::number` | `sl.types::int`    | `sl.types::number` |
| `sl.types::int`    | `sl.types::int`    | `sl.types::int`    |
| `sl.types::int`    | `sl.types::number` | `sl.types::number` |

The minus operator consists of a minus sign (`-`) and subtracts the second operand from the first. It returns the result
of the subtraction.

### 3.1.2.3 The multiplication operator

| Operand 1 type     | Operand 2 type     | Result type        |
|--------------------|--------------------|--------------------|
| `sl.types::number` | `sl.types::number` | `sl.types::number` |
| `sl.types::number` | `sl.types::int`    | `sl.types::number` |
| `sl.types::int`    | `sl.types::int`    | `sl.types::int`    |
| `sl.types::int`    | `sl.types::number` | `sl.types::number` |

The multiplication operator consists of an asterisk (
`*`) and multiplies the two operands. It returns the product of the two operands.

### 3.1.2.4 The division operator

| Operand 1 type     | Operand 2 type     | Result type        |
|--------------------|--------------------|--------------------|
| `sl.types::number` | `sl.types::number` | `sl.types::number` |
| `sl.types::number` | `sl.types::int`    | `sl.types::number` |
| `sl.types::int`    | `sl.types::int`    | `sl.types::int`    |
| `sl.types::int`    | `sl.types::number` | `sl.types::number` |

The division operator consists of a slash (
`/`) and divides the first operand by the second. It returns the quotient of the two operands.

if the second operand is `0`, `0` is returned.

### 3.1.2.5 The modulo operator

| Operand 1 type     | Operand 2 type     | Result type        |
|--------------------|--------------------|--------------------|
| `sl.types::number` | `sl.types::number` | `sl.types::number` |
| `sl.types::number` | `sl.types::int`    | `sl.types::number` |
| `sl.types::int`    | `sl.types::int`    | `sl.types::int`    |
| `sl.types::int`    | `sl.types::number` | `sl.types::number` |

The modulo operator consists of a percent sign (
`%`) and divides the first operand by the second and returns the rest of the division.

If the second operand is `0`, `0` is returned.

### 3.1.2.6 The increment operator

This operator only takes one operand on the left side.

| Operand type       | Result type        |
|--------------------|--------------------|
| `sl.types::number` | `sl.types::number` |
| `sl.types::int`    | `sl.types::int`    |

The increment operator consists of two plus signs (`++`) and adds `1` to the operand. It returns the result of the sum.

### 3.1.2.7 The decrement operator

This operator only takes one operand on the left side.

| Operand type       | Result type        |
|--------------------|--------------------|
| `sl.types::number` | `sl.types::number` |
| `sl.types::int`    | `sl.types::int`    |

The decrement operator consists of two minus signs (`--`) and subtracts
`1` from the operand. It returns the result of the subtraction.

### 3.1.2.8 The power operator

| Operand 1 type     | Operand 2 type     | Result type        |
|--------------------|--------------------|--------------------|
| `sl.types::number` | `sl.types::number` | `sl.types::number` |
| `sl.types::number` | `sl.types::int`    | `sl.types::number` |
| `sl.types::int`    | `sl.types::int`    | `sl.types::int`    |
| `sl.types::int`    | `sl.types::number` | `sl.types::number` |

The power operator consists of a caret (
`^`) and raises the first operand to the power of the second. It returns the result of the power.

## 3.1.3 Logical operators

Logical operators all return an object of type [
`sl.types::bool`](TBD.md). They perform logical operations on the operands.

### 3.1.3.1 The and operator

| Operand 1 type   | Operand 2 type   | Result type      |
|------------------|------------------|------------------|
| `sl.types::bool` | `sl.types::bool` | `sl.types::bool` |

The and operator consists of two ampersands (`&&`) and compares the two operands. It returns `1` if both operands are
`1` and `0` if one or both operands are `0`.

If the left operand is `0`, the right operand will not be evaluated.

### 3.1.3.2 The or operator

| Operand 1 type   | Operand 2 type   | Result type      |
|------------------|------------------|------------------|
| `sl.types::bool` | `sl.types::bool` | `sl.types::bool` |

The or operator consists of two vertical bars (`||`) and compares the two operands. It returns
`1` if one or both of the operands are`1` and `0` if both operands are `0`.

### 3.1.3.3 The not operator

This operator only takes one operand on the right side.

| Operand type     | Result type      |
|------------------|------------------|
| `sl.types::bool` | `sl.types::bool` |

The not operator consists of an exclamation mark (`!`) and compares the operand. It returns `1` if the operand is
`0` and `0` if the operand is `1`.

<note>
As an exclamation mark at the beginning of a statement will be evaluated as a return statement, beginning with an exclamation mark must be put in parentheses.

<code-block>
// This returns the test variable
!test;
// This negates the test variable
(!test);
</code-block>
<warning>
The second example has no effect though.
</warning>
</note>

## 3.1.4

## 3.1.5 Parentheses

Parentheses are used to group expressions. They are also used to define the order of operations. The expression inside
the parentheses is evaluated first.

**Example**:

```
sl::io.out(1 + 2 * 3); // Outputs 7
sl::io.out((1 + 2) * 3); // Outputs 9
```

## 3.1.6 Evaluation order

The evaluation order of operators is defined by the following table. The operators are ordered from highest to lowest
precedence.

| Num | Operator | Description           |
|-----|----------|-----------------------|
| 0   | `=`      | Assignment            |
| 0   | `+=`     | Plus equals           |
| 0   | `-=`     | Minus equals          |
| 1   | `()`     | Parentheses           |
| 2   | `>`      | Greater than          |
| 2   | `>=`     | Greater than or equal |
| 2   | `<`      | Less than             |
| 2   | `<=`     | Less than or equal    |
| 2   | `==`     | Equals                |
| 2   | `!=`     | Not equals            |
| 3   | `^`      | Power                 |
| 4   | `++`     | Increment             |
| 4   | `--`     | Decrement             |
| 5   | `!`      | Not                   |
| 6   | `*`      | Multiplication        |
| 6   | `/`      | Division              |
| 7   | `%`      | Modulo                |
| 8   | `+`      | Addition              |
| 8   | `-`      | Subtraction           |
|     | `&&`     | And                   |
|     | `\|\|`   | Or                    |

The left operand of an operator is always evaluated first, then the right operand. For operators with the same precedence the evaluation order is from left to right.