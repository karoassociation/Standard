# 1.6 Type restrictions

A special property of Karo is to restrict certain types to certain values. This is done by putting the restrictions between single quotes after the type.

These restrictions are constrained to comparisons with the operators `==`, `!=`, `|>`, `!|>`, `>`, `>=`, `<` and `<=`. One constraint consists of a property name of the type, an operator and a following value.
Values can be strings as described in [](3-7-Strings.md) or a number as described in 

**Example:**

Following a list of examples of type restrictions. The explanations are in the comments.

```
// Define a variable of type int with the restriction that the value must be between 0 and 10 (inclusive).
a: int'value >= 0 && value <= 10' = 5;
// Define a variable of type array with explicit length of 5 (that contains integers that are either 0 or 2).
b: array<int'value == 0 || value == 2'>'length == 5' = [0, 2, 0, 2, 0];
// Define a variable that contains a string that is either "Hello" or "World".
c: string'value == "Hello" || value == "World"' = "Hello";
```

## 1.6.1 Assigning to a restricted type

You can always assign a value to a restricted type if the value is of the type of the restriction or a less restricted type.

**Example:**

Following an example of assigning to a restricted type.

```
// Assign a value of type int to a variable of type int with the restriction that the value must be between 0 and 10 (inclusive).
a: int'value >= 0 && value <= 10' = 5;
b: int'value >= 0 && value <= 8' = 3;
// This is a valid assignment as the value is of the type of the restriction.
a = b;
// This is not a valid assignment as the value is not of the type of the restriction.
b = a;
```