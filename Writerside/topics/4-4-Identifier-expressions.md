# 4.4 Identifier expressions

An identifier expression describes a property name. There are several ways to describe the way to access the property. If its ambiguous which property is meant, the one of the top-most scope is taken.

Type names can be specified with their namespace path or just with their name, later only if the name is not overridden in the current scope.

## 4.4.1 Single identifier

A single identifier is just a name of a property. It can be a local variable, a function parameter, a type member, a static member of a type or a type name.

## 4.4.2 Namespace path

A type name can be specified with its namespace path. The path elements are separated by dots (`.`) followed by a double colon (`::`) and the type name.

**Example:**
```
// Type "test" in the namespace "my.namespace"
my.namespace::test;
```
## 4.4.3 Static property access

Static members (described in [](2-2-Static-members.md)) can be accessed via a single colon after a type or a member of the type
`sl.types::type`. The colon will be replaced with as an index to the member `staticFields` of the type.

Functions are accessed as properties with names described in [](1-2-Functions.md#1-2-3-function-names).

**Example:**

```
// Accesses the static member `empty` in the type `sl.types::string`
sl.types::string:empty;

// The above is equivalent to the following
sl.types::string.staticFields["empty"];

// Other example: Function
sl::internal:typeOf("test");

// Translates to
sl.types::function<sl.types::void, sl.types::string> f := sl::internal.staticFields["typeOf(sl.types::string)"];
f("test");
```

## 4.4.4 Class property access

The member properties of a class (not static members) are accessed via a dot (`.`) after an instance of a class.

**Example:**

```
// Accesses the member `length` in the instance `myString` of the type `sl.types::string`
myString.length;
```
