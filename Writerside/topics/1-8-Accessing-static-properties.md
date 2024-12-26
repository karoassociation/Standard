# 1.8 Accessing static properties

Static members (described in [2.2 Static members](2-2-Static-members.md)) can be accessed via a single colon after a type or a member of the type `sl.types::type`. The colon will be replaced with as an index to the member `staticFields` of the type.

Functions are accessed as properties with names described in [1.2.3 Function names](1-2-Functions.md#1-2-3-function-names).

**Example:**

```
// Accesses the static member `empty` in the type `sl.types::string`
sl.types::string:empty;

// The above is equivalent to the following
sl.types::string.staticFields["empty"];

// Other example: Function
sl::internal:typeOf("test");

// Translates to
sl::internal.staticFields["typeOf(sl.types::string)"]
```
