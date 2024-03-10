# 2 Objects

In Karo everything is an object. Every object has a type and a value. The type defines what the object can do and the
value is the actual data that the object holds.

A type is defined by a class. A class is a collection of properties and methods (Although methods are also properties,
but they are called methods to differentiate them from other properties). An uninitialized class is called a Type (and
is a class itself from type `sl.types::type`). A class can be initialized by calling the constructor of the class. The
constructor is a method with the same name as the class. A class can have multiple constructors, but only one can be
called at a time. The constructor is called when the class is initialized. The constructor can be called with arguments.
The arguments are defined in the constructor definition. The constructor can also be called without arguments. In this
case the default constructor is called. The default constructor is the constructor without arguments.