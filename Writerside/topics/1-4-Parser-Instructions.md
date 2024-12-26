# 1.4 Parser Instructions

<code-block src="definitions.txt" include-lines="6-8" />

Parser instructions are instructions executed at compile time by the compiler. You start a parser instruction with a hash symbol and end it with a semicolon. It consists of two parts, first the parser instruction name and then separated by a space the parser instruction content. The later one being optional. There are no syntactical rules for the content.

The standard defines several parser instructions outlined in the following sections but a parser or a compiler can define their own, although it is highly encouraged to contribute them to the standard.

> If the compiler or the interpreter encounters an unknown instruction it should throw a warning or ignore it. An
> unknown parser instruction should not prevent compiling.
>
{style="warning"}

## 1.4.1 Entry point instruction

```
#entrypoint;
```

This instruction indicates that the function that is defined next in the current class will be the entrypoint of the application. It has to be directly before the function (so after the attributes). This function will be called as the first one, when the compiled application starts. Only one entry point can be defined.

**Example:**
This example defines a function that outputs Hello World as the entry point of the application.

```
testNamespace::testClass {
    [constructor]
    #entrypoint; || {
        sl.io.out("Hello World");
    }
}
```

> Depending on the usage of the interpreter or the compiler, they can also decide that no entry point is allowed and
> throw an error.
>
{style="note"}

## 1.4.2 Import instruction

```
#import {filename};
```

[TBD]

## 1.4.3 Make static function/property accessible everywhere

```
#makeStaticAvailableEverywhere {identifierOfStaticProperty};
```

This parser instruction takes a name of a static property, which will make it then universally available by the properties name. If a property with the same name already exists, its definition will be overwritten.
