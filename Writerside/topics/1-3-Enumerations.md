# 1.3 Enumerations

Enumerations (objects of the type
`sl.types::enumeration`) are collections of values which can be assigned to variables of this specific type. Every value is based on

<code-block src="definitions.txt" include-lines="3,5" />

## 1.3.1 Defining an enumeration

Enumerations can be defined in place of a class, so the same rules concerning attributes, namespace, name and definition file apply. Please [TBD] to see how to define a class.

The only difference is that `<-` is put before the namespace name.

After that come the enumeration contents enclosed by angle brackets and separated with commas. The list can end with a trailing comma.

**Example**:

The following example defines an enumeration of different colors.

```
<-examples.ColorNamespace::Color {
    green,
    red,
    blue,
    lightBlue
}
```

## 1.3.2 Define an underlying type

[TBD]

## 1.3.3 Set specific values for entries

[TBD]