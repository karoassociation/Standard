# 3.2 Pipe statements

<code-block lang="BNF" src="definitions.bnf" include-lines="35"></code-block>

There are two types of pipe statements: Variable assignment statement and argument passing statement. A pipe statement consists of a left statement, the pipe operator (`->`) and then a statement or another pipe statement on the right.

<warning>
As specified in <a href="A-1-Definitions-txt.md"></a> a pipe statement cannot be used in a variable assignment statement or inside of parenthesis.
</warning>

## 3.2.1 Variable assignment

The pipe statement allows to assign a new value to an existing property or a variable. The statement on the left side will be evaluated and assigned to the identifier specified on the right side.

You cannot assign to a property which is marked with the `sl.attributes::readOnly` attribute unless it is in a function marked with the `sl.attributes::constructor` attribute. If the property has the `sl.attributes::readOnly` and the `sl.attributes::static` attribute it can only be assigned in a method with `sl.attributes::static` attribute and the `sl.attributes::constructor` attribute.

**Example:**

<code-block>
test: sl.types::number := 10;
// Assign 810 to the variable "test"
800 + test -> test;
</code-block>

A variable assignment pipe statement returns `sl.types::void`, that means it cannot be used in a further pipe statement.

## 3.2.2 Argument passing

In this type of statement the left side of the pipe operator will be evaluated and then passed as the first argument of the first function called on the right side.

If the right side does not use a function call, the compiler or interpreter should throw an error.

**Example:**

<code-block>
// "Hello World" will be passed as the first argument in the "sl::io:out()" function.
"Hello " + "World" -> sl::io:out();
</code-block>