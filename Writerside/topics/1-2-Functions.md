# 1.2 Functions

<show-structure for="chapter" depth="5"></show-structure>

<code-block lang="BNF" src="definitions.bnf" include-lines="13-16" />

Functions (Classes with the type [`sl.types.function<ReturnType, ParameterTypes[]>`](TBD.md) (where `ReturnType` is the return type and the `ParameterTypes` array contains all the types of the parameters)) contain a series of [statements](3-Statements.md) that can be called with parameters.

## 1.2.1 Defining functions

Inside a type functions can be defined as properties with a special syntax.

A function definition consists of three elements: The parameters list, the return type and the function body with the statements.
The parameter list is optional and can be blank.

A function defined in a type will always be assumed to have been marked with the `sl.attributes::static` attribute unless the function has a first parameter that is a class reference parameter (see [class reference parameter](#1-2-1-1-3-class-reference-parameter)).
An exception to this rule are functions that have the `sl.attributes::constructor` attribute. These functions will always be assumed to be non-static unless they also have the `sl.attributes::static` attribute.

### 1.2.1.1 Parameter list

The parameter list is enclosed with vertical bars. The parameters are separated by a comma (trailing comma is not allowed). For a parameter first comes the name of the variable that will store the passed parameter. After that comes a colon and after that the type definition of the parameter.

A function marked with the `sl.attributes::constructor` and the `sl.attributes::static` attribute cannot have any parameters.

**Example:**

The following example defines a function with two parameters: a boolean and a number (Please consider that this is an incomplete example as the return type and the statements are missing):

```
|a: bool, b: number|
```

#### 1.2.1.1.1 Optional parameters

[TBD](TBD.md)

#### 1.2.1.1.2 Variadic parameter

A function can be defined with the last parameter being a variadic parameter. This is done by prefixing the type declaration with three dots (`...`).
A variadic parameter can be used to pass a variable number of parameters of the same type. The variadic parameter will be passed as an array of the specified type.

The variadic parameter type must be of `sl.types::array<type>` where `type` is the type of the variadic parameter.

If a function is defined with variadic parameters. no other function with the same name can be defined with a different number of parameters.

#### 1.2.1.1.3 Class reference parameter

If a function is defined in a class, the first parameter can be a reference to the class itself. This is done by specifying an exclamation mark as the type declaration. This reference can be used to access the class properties and methods. This type of parameter is not allowed in static functions.

**Example:**


The following example defines a function with two parameters, where the first one is a reference to the class itself (as the previous examples, this is incomplete).

```
|this: !, a: bool|
```

### 1.2.1.2 Return type

The return type defines the type of the value the function returns. It is defined by a colon followed by the type.

A function marked with the `sl.attributes::constructor` attribute must have `sl.types::void` as return type.

**Example:**

The following example defines two functions (one with a parameter list, the second one without a parameter list) (these examples are incomplete).

```
|a: bool|: int
: int
```

### 1.2.1.3 Statements

The statements are enclosed between angle brackets and separated by semicolons. All statements (also the last one) must be ended with a semicolon.

**Example:**

The following example creates a function that adds two numbers (passed as parameters) together and returns them. The first parameter can also be passed as a pipe input.

```
|firstNumber: number, secondNumber: number|: number {
    !firstNumber + secondNumber;
}
```

## 1.2.1.4 Generic functions

A function can be made generic by appending a less-then symbol (`<`), a type parameter list and then a greater-then symbol (`>`) after the function name.
The type parameter list is a comma-separated list of type parameter names.
The defined parameter names can be used everywhere in the function definition. Type parameter names must be unique within the function definition.
More than one function with the same name can be defined as long as they have a different number of type parameters (including zero).

A function marked with the `sl.attributes::constructor` attribute can not be made generic.

## 1.2.2 Calling functions

A function is called by calling the function object (see [](4-2-Calling-expressions.md)). The parameters that are passed in correspond to the parameters that are defined in the function definition. The return value of the function is the value of the function object.

## 1.2.3 Function names

Behind the scenes of the compiler/interpreter the function names are generated to make a unique name, so they can be accessed with different parameters.

This is only done for functions that are defined in a type directly.

> That means functions that are defined like a type property (**Example**: `testProperty: function<void> := ||: void { }`) are not affected by this. They will have the name that is defined in the type.

They are structured as following:

* Function name:
    * For named function: The name of the function
    * Function that has the `sl.attributes::constructor` attribute and no `sl.attributes::static` attribute: `*constructor`
    * Function that has the `sl.attributes::constructor` attribute and the `sl.attributes::static` attribute: `*staticConstructor`
    * For other functions with no name: `*Backfield` and then the number of the anonymous function in the current type
* For generic functions: `` ` ``, then the number of type parameters
    * For variadic type parameters the variadic is not counted and `...` is added after the number
* Parameter list: `(`The parameters with full qualifier separated by a comma (`)`)
    * For variadic parameters use `...` followed by the type

**Examples:**

Following some function definitions. First the full name and then the corresponding function definition.

```
//example(sl.types::int,sl.types::string,...sl.types::array<sl.types::string>)
example |a:int, b: string, c: ...string[]|: void { }

//<>1:2...:()
<T1, T2, ...T>||: string { }
```
