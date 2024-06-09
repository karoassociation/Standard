# 3.2 Calling

<code-block src="definitions.txt" include-lines="10" />

Calling is invoked in a statement if an identifier is provided directly followed by an opening parenthesis. After that comes a comma separated list of arguments. The list is enclosed by a closing parenthesis.

Calling an identifier invokes the function of the type of the identifier which has the attribute `sl.attributes::invokable`. The function is invoked with the arguments provided in the parentheses. The arguments are evaluated from left to right and are passed by value.

The return value of this statement type is the return value of the invoked function.

## 3.2.1 Calling a function

Calling a function (an object of type `sl.types::function`) is a special case of calling. You can only pass the in the function definition provided function argument types. The return value of the function is the return value of the statement.

## 3.2.2 Calling a type

Calling a class (an object of type `sl.types::type`) is a special case of calling. You can only pass the in the constructor definition provided constructor argument types. The return is the initialized class.
