# 3.3 Array access

<code-block src="definitions.txt" include-lines="21" />

Array access is invoked in a statement if an identifier is provided directly followed by an opening square bracket. After that comes an expression which is closed by a closing square bracket.

Accessing an identifier invokes the function of the type of the identifier which has the attribute `sl.attributes::arrayAccess`. The function is invoked with the expression provided in the square brackets. The expression is evaluated and passed by value. The return value of this statement type is the return value of the invoked function.