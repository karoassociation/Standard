# 2.4 Constructors

Constructors are special functions that have the `sl.attributes::constructor` attribute.
They are used to initialize a class of a type or to initialize the static properties of a type.

## 2.4.1 Class constructor

A class constructor is a function that has the `sl.attributes::constructor` attribute and no `sl.attributes::static` attribute. It has the same capabilities as a normal function, but it must have a return type of `sl.types::void`.

The compiler/interpreter must ensure that all overloads of the constructor must initialize all uninitialized properties of the type before the constructor ends.

Furthermore, a class constructor can use uninitialized properties of the type to assign values. It is in the responsibility of the interpreter/compiler to ensure that the properties are initialized before they are used.

At the start of any constructor all non-static property initializers are executed in the order they are defined in the class.

## 2.4.2 Static constructor

A static constructor is a function that has the `sl.attributes::constructor` attribute and the `sl.attributes::static` attribute.

It has the same capabilities as a normal function, but it must have a return type of `sl.types::void` and no parameters (Therefore only one such function can exist).

A static constructor is used to initialize static properties of a type. The compiler/interpreter must ensure that all static properties that are not initialized with a property initializer are initialized in the static constructor before it ends.

At the start of the static constructor all static property initializers are executed in the order they are defined in the class.

A static constructor shall be called automatically before the first instance of the type is created or any static members are referenced.

If a type is generic, the static constructor is called for each instantiation of the generic type.
