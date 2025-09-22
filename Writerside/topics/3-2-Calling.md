# 3.2 Calling

<code-block lang="BNF" src="definitions.bnf" include-lines="10" />

Calling is invoked in a statement if an identifier is provided directly followed by an opening parenthesis. After that comes a comma separated list of arguments. The list is enclosed by a closing parenthesis.

Calling an identifier invokes the function of the type of the identifier which has the attribute `sl.attributes::invokable`. The function is invoked with the arguments provided in the parentheses. The arguments are evaluated from left to right and are passed by value.

The return value of this statement type is the return value of the invoked function.

## 3.2.1 Calling a function

Calling a function (an object of type `sl.types::function`) is a special case of calling. You can only pass the in the function definition provided function argument types. The return value of the function is the return value of the statement.

## 3.2.2 Calling a type

Calling a class (an object of type `sl.types::type`) is a special case of calling. You can only pass the in the constructor definition provided constructor argument types. The return is the initialized class.

## 3.2.3 Construct calling

If the call is directly followed by an anonymous function definition (see [](3-9-Anonymous-functions.md)) the function will be invoked with the provided arguments and the anonymous function as the last argument.

**Example:**

This calls the internally named function `myFunction(sl.types::number, sl.types::string, sl.types::function<sl.types::void, sl.types::number>)`:

<code-block>
myFunction(10, "Hello") |result: number|: void { };
</code-block>

The arguments `10` and `"Hello"` are passed as the first two arguments and the anonymous function as the third argument.

### 3.2.3.1 Construct calling anonymous function return statement

If an anonymous function is defined in a construct calling context, the return type should be treated like it is called from the surrounding function.
If a construct calling occurs in an anonymous function that is also part of a construct calling, the return type should be treated like it is called from the topmost construct calling context.
If a construct call is used in a property definition, using a return statement is not allowed.

This implies that the return type if a construct calling anonymous function is always `sl.types::void`.

**Example:**

Here the two anonymous functions for the `sl::constructs:if` and the `sl::constructs:else` functions do not return the values of their respective return statements, but `sl.types::void`. The return statement is directly passed to and executed on the `testFunction` function.

<code-block lang="plain text">
    testFunction ||: bool {
        test: string := "hello";
        if (test == "hello") {
            !true;
        } -> else() {
            !false;
        }
    }
</code-block>
