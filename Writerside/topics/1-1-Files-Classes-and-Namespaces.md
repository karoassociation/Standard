# 1.1 Files, Types and Namespaces

<code-block src="definitions.txt" include-lines="1-2,4,11-12,27" />

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

The null character (Hex code: 0) is not allowed and if the compiler or the interpreter encounters it they should
throw an error.

### 1.1.1.1 MIME-Type

<primary-label ref="ns"/>

The files should have the mime-type "Text/Karo" if possible.

## 1.1.2 Namespaces

A namespace is the directory structure from the path where the file is located (from the project root as starting point). The path elements are separated by a dot (with no trailing dot at the end).

> How a project root is defined can be determined by the compiler or the parser.
>
{style="note"}

**Example**:

A file located under `exampleProject/example/tests/` has the namespace `exampleProject.example.tests`.

## 1.1.3 Types

A type is a container of properties. Multiple instance of the same type can exist (unless it is a static type). These instances are called classes.