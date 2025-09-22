# 2.3 Generic types

A type can be made generic by appending a less-then symbol (`<`), a type parameter list and then a greater-then symbol (`>`).

A type parameter list is a comma-separated list of type parameter names.

Generic types allows creating classes with variable type parameters. The defined parameter names can be used everywhere in the type definition. Type parameter names must be unique within the type definition.

More than one type with the same name can be defined as long as they have a different number of type parameters (including zero).

## 2.3.1 Variadic type parameters

A type parameter can be made variadic by prefixing the last type parameter name with three dots (`...`). A variadic type parameter can be used to define a variable number of type parameters. A variadic type parameter must be the last type parameter in the type parameter list.
A variadic type parameter will produce an accessible array of types with the specified type names. A variadic type parameter cannot be the only type parameter.

If a type is defined with a variadic type parameter, it can be instantiated with any number of type parameters, minimum the number of non-variadic type parameters.

If a type is defined with a variadic type parameter, there cannot be another type with the same name and different number of type parameters (including zero).

## 2.3.2 Internal names

A generic type will set the internal type name to the type name appended with a backtick (`` ` ``) and the number of type parameters. If a variadic type parameter is used, three dots (`...`) will be appended to the number of type parameters (the variadic parameter is not counted).
