# 1.2 Functions

<show-structure for="chapter" depth="5"/>

<code-block src="definitions.txt" include-lines="13-16" />

Functions (Objects with the type [`sl.types.function<ReturnType, ArgumentsTypes[]>`](TBD.md) (where `ReturnType` is the return type and the `ArgumentsTypes` array contains all the types of the arguments)) contain a series of [statements](3-Statements.md) that can be called with arguments.

## 1.2.1 Defining functions

A function consists of three elements: The arguments list, the return type and the function body with the statements.
The argument list is optional and can either be omitted or blank.

### 1.2.1.1 Argument list

The argument list is enclosed with vertical bars. The arguments are separated by a comma (trailing comma is not allowed). For an argument first comes the name of the variable that will store the passed argument. After that comes a colon and after that the type definition of the argument.

**Example:**

The following example defines a function with two arguments: a boolean and a number (Please consider that this is an incomplete example as the return type and the statements are missing):

```
|a: bool, b: number|
```

#### 1.2.1.1.1 Optional arguments

[TBD]

#### 1.2.1.1.2 Piped arguments

[TBD]: Link to pipe explanation

If you want to accept one argument value from a pipe you can add `<-` before the type declaration (but after the colon).
Only one such argument is allowed.

**Example:**

The following example defines a function with two arguments, where the second one accepts a pipe  (as the previous examples, this is incomplete).

```
|a: bool, b: <-number|
```

#### 1.2.1.1.3 Class reference

If a function is defined in a class, the first argument can be a reference to the class itself. This is done by specifying an exclamation mark as the type declaration. This reference can be used to access the class properties and methods. This type of argument is not allowed in static functions.

> The compiler or the interpreter should convert this argument type to the type `sl.types::classReference<t>` where `t`
> is the type of the class.
> {style="info"}

**Example:**


The following example defines a function with two arguments, where the first one is a reference to the class itself (as the previous examples, this is incomplete).

```
|this: !, a: bool|
```

### 1.2.1.2 Return type

The return type defines the type of the value the function returns. It is defined by a colon followed by the type.

**Example:**

The following example defines two functions (one with a parameter list, the second one without a parameter list) (these examples are incomplete).

```
|a: bool|: int
: int
```

### 1.2.1.3 Statements

The statements are enclosed between angle brackets and separated by semicolons. All statements (also the last one) must be ended with a semicolon.

**Example:**

The following example creates a function that adds two numbers (passed as arguments) together and returns them. The first parameter can also be passed as a pipe input.

```
|firstNumber: number, secondNumber: number|: number {
    !firstNumber + secondNumber;
}
```

## 1.2.2 Calling functions

A function is called by calling the function object (see [3.2 Calling](3-2-Calling.md)). The arguments that are passed in correspond to the arguments that are defined in the function definition. The return value of the function is the value of the function object.

## 1.2.3 Function names

Behind the scenes of the compiler/interpreter the function names are generated to make a unique name, so they can be accessed with different arguments.

They are structured as following:

* Function name:
  * For named function: The name of the function
  * Function that has the `sl.attributes::constructor` attribute. `<c>`
  * For other functions with no name: `<>` and then the number of the anonymous function in the current type
* For generic functions: `:`, then the number of generic functions, `:`
  * For variadic type arguments the variadic is not counted and `...` is added after the number
* Argument list: `(`The arguments with full qualifier seperated by a comma (`)`)
  * For varidic arguments use `...` followed by the type
* Then `*` and the fully qualified return type

**Examples:**

Following some function definitions. First the full name and then the corresponding function definition.

```
//example(sl.types::int,sl.types::string,...sl.types::array<sl.types::string>)*sl.types::void
example |a:int, b: string, c: ...string[]|: void { }

//<>1:2...:()*sl.types::string
<T1, T2, ...T>||: string { }
```