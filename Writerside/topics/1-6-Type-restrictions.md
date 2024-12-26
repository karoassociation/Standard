# 1.6 Type restrictions

A special property of Karo is to restrict certain types to a certain values. This id done by putting the restrictions in single quotes after the type.

You compare a value to a property of a type.

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