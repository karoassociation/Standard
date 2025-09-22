# 1.4 Parser Instructions

<code-block lang="BNF" src="definitions.bnf" include-lines="6-8" />

Parser instructions are instructions executed at compile time by the compiler. You start a parser instruction with a hash symbol and end it with a semicolon. It consists of two parts, first the parser instruction name and then separated by a space the parser instruction content. The later one being optional. There are no syntactical rules for the content.

The standard defines several parser instructions outlined in the following sections but a parser or a compiler can define their own, although it is highly encouraged to contribute them to the standard.

> If the compiler or the interpreter encounters an unknown instruction it should throw a warning or ignore it. An
> unknown parser instruction should not prevent compiling.
>
{style="warning"}

Inside the parser instruction content, you can use the following escape sequences:

| Escape sequence | Evaluates to                     |
|-----------------|----------------------------------|
| `\;`            | Semicolon (`;`)                  |
| `\\`            | Backslash (`\`)                  |

## 1.4.1 Entry point instruction

```
#entrypoint;
```

This instruction indicates that the function that is defined next in the current class will be the entrypoint of the application. It has to be directly before the function (so after the attributes). This function will be called as the first one, when the compiled application starts.
Only one entry point must be defined.
If the enclosing type is a generic type, its type parameters cannot be used in the entry point function.
The entry point function must not have any parameters and must have a void return type.

**Example:**
This example defines a function that outputs Hello World as the entry point of the application.

```
testNamespace::testClass {
    [constructor]
    #entrypoint; ||: void {
        sl.io:out("Hello World");
    }
}
```

> Depending on the usage of the interpreter or the compiler, they can also decide that no entry point is allowed and
> throw an error.
>
{style="note"}

## 1.4.2 Import instruction

```
#import {importNamespaceOrClass};
```

An import instruction imports either a type directly or all types of a namespace based on whatever is specified. The imported types can then be used in the whole file.

The import parser instruction is only valid before any types are used.

> That means you cannot use an import instruction after using an attribute or using the makeStaticAvailableEverywhere instruction.

**Example**:

```
// Import the sl.types::bool type.
#import sl.types::bool;

// Import all types in the sl.attributes namespace
#import sl.attributes;

```

## 1.4.3 Make static function/property accessible everywhere

```
#makeStaticAvailableEverywhere {identifierOfStaticProperty};
```

This parser instruction takes a name of a static property, which will make it then universally available by the properties name. If a property with the same name already exists, its definition will be overwritten.

## 1.4.4 Emit warning
```
#warning {warningText};
```

This parser instruction lets the compiler or the interpreter emit a warning at the position of the parser instruction.

## 1.4.5 Emit error
```
#error {errorText};
```

This parser instruction lets the compiler or the interpreter emit an error at the position of the parser instruction. This stops the compilation or the execution of the interpreter.
