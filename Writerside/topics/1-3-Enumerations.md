# 1.3 Enumerations

Enumerations (objects of the type [`sl.types.enumeration`](TBD.md)) are collections of values.

<code-block src="definitions.txt" include-lines="3,5" />

## 1.3.1 Defining an enumeration

Enumerations can be defined in place of a class, so the same rules concerning attributes, namespace, name and
definition file apply. Please [TBD] to see how to define a class.

The only difference is that `!` is put before the namespace name.

> The exclamation mark is a reference to the return statement operator.

After that come the enumeration contents enclosed by angle brackets and separated with commas (no trailing comma at
the end allowed).

**Example**:

The following example defines an enumeration of different colors.

```
!examples.ColorNamespace::Color {
    green,
    red,
    blue,
    lightBlue
}
```