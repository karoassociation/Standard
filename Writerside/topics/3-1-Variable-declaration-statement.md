# 3.1 Variable declaration statement

<code-block lang="BNF" src="definitions.bnf" include-lines="34"></code-block>

To define a new variable in the current function scope you need to use a variable decleration statement. Every variable has a name and a type. There cannot be two variables with the same name in the same context.

The syntax is as following: First a name is defined, followed by a colon (
`:`), then the type the variable will have, the assignment operator (a colon followed by an equals sign (
`:=`)) and at last the statement which first will be assigned to the variable.