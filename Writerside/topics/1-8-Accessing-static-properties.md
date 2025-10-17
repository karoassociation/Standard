# 1.8 Scopes

A scope defines the visibility of 

1. Root scope with all fully qualified type names (that means with their namespace path) of the imported namespaces and types
2. General scope that includes all with the `makeStaticAvailableEverywhere` parser instruction imported types (described in [](1-4-Parser-Instructions.md#1-4-3-make-static-function-property-accessible-everywhere))
3. Namespace scopes from the current namespace up to the root namespace with all type names (that means without their namespace path) (Upper namespaces override lower namespaces)
4. Current type scope with all static members of the current type
5. Local scopes that are created by functions and anonymous functions (inner scopes override outer scopes)
