# 1.1 Files, Types and Namespaces

<code-block lang="BNF" src="definitions.bnf" include-lines="1-2,4,11-12,27" />

> When this document speaks of classes in the sense of how to define their names, namespaces and their one class per
> file constraint it also means Enumerations. Look at [1.3 Enumeration](1-3-Enumerations.md) for more information.
>
{style="warning"}

In Karo the directory structure defines the namespaces and one file contains one single class or one single enumeration.

## 1.1.1 Files

Karo source code files have a filename ending with the extension `.karo`. The files contain the source code in raw text form. A file contains optional parser instructions and one optional class definition.

> Empty files or files with just parser instructions are allowed, but it is discouraged from using them.
>
{style="note"}

The following characters are not allowed and if the compiler or the interpreter encounters them they should throw an error:

| Character    | Unicode code point |
|--------------|--------------------|
| NULL         | U+0000             |
| Alert        | U+0007             |
| Backspace    | U+0008             |
| Escape       | U+001B             |
| Form feed    | U+000C             |
| Vertical tab | U+000B             |

### 1.1.1.1 MIME-Type

<primary-label ref="ns"/>

The files should have the mime-type "Text/Karo" if possible.

### 1.1.1.2 Shebang

If a file starts with a hash character followed by an exclamation mark (`#!`) the first line of the file shall be ignored.

## 1.1.2 Namespaces

A namespace is the directory structure from the path where the file is located (from the project root as starting point). The path elements are separated by a dot (with no trailing dot at the end).

> How a project root is defined can be determined by the compiler or the parser.
>
{style="note"}

**Example**:

A file located under `exampleProject/example/tests/` has the namespace `exampleProject.example.tests`.

## 1.1.3 Types

A type is a container of properties. Multiple instance of the same type can exist (unless it is a static type). These instances are called classes.

### 1.1.3.1 Boxed types

Certain built-in types are boxed types that contain in addition to their properties an underlying value.

Following are all the built-in types which are considered boxed.

| Name:                                     | Boxes the value:                                                                   |
|-------------------------------------------|------------------------------------------------------------------------------------|
| `sl.types::string`                        | An UTF-16 encoded string of variable length.                                       |
| `sl.types::number`                        | An integer value (preferably 64-bit if possible).                                  |
| `sl.types::float`                         | An IEEE 756 floating point precision number.                                       |
| `sl.types::array<T>`                      | An continuous row of elements of type `T`.                                         |
| `sl.types::function<ReturnValue, ...T[]>` | A function with a return value of `ReturnValue` and parameters of the types `T[]`. |
| `sl.types::action<...T[]>`                | A function with no return value and parameters of the types `T[]`.                 |
| `sl.types::type`                          | A karo type.                                                                       |