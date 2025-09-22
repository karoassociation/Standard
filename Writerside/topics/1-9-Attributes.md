# 1.9 Attributes

Attributes denote special properties or metadata about types, enums or properties of types.

## 1.9.1 Attribute syntax

Attributes are specified between square brackets (`[]`) before the definition of a type, enum or property.

Specifying an attribute is calling the constructor of the type provided as attribute.
The specified type must implement the `sl.attributes::attribute` interface. The parentheses may be omitted if no arguments should be passed to the constructor.

All the passed arguments are passed directly by value. Referencing properties of any kind is not possible, except for enum values.

## 1.9.2 Defining an attribute

A type that implements the `sl.attributes::attribute` interface can be used as an attribute. It must only define functions with the `sl.attributes::constructor` attribute, that don't have the `sl.attributes::static` attribute.
The types of the parameters of the constructor function must be one of the following types:
* A type that inherits from `sl.types::enum`.
* `sl.types::string`
* `sl.types::number`
* `sl.types::bool`
* `sl.types::float`

An attribute type can also specify the need for type parameters.