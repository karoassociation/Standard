# 1.8 Accessing static members

Static members (described in [2.2 Static members](2-2-Static-members.md)) can be accessed via a single colon after a type or a member of the type `sl.types::type`. The colon will be replaced with a call to the member `staticMembers` of the type.

**Example:**

```
// Accesses the static member `empty` in the type `sl.types::string`
sl.types::string:empty;

// The above is equivalent to the following
sl.types::string.staticMembers.empty;
```
