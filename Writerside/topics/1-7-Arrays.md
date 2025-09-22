# 1.7 Arrays

<code-block lang="BNF" src="definitions.bnf" include-lines="32" />

Arrays are continuous collections of items of the same type (or type inheriting from it).

## 1.7.1 Array type

When putting square brackets (`[]`) after a type name it will become be transformed to the type `sl.types::array<T>` with the original type as first generic parameter. This pseudo-operator is always left-associative, so `type[][]` is equivalent to `sl.types::array<sl.types::array<type>>`.

## 1.7.2 Array mutations

The items of an array can be reassigned, but it is not possible to shorten or lengthen an already created array type.