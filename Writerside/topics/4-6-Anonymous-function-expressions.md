# 4.6 Anonymous function expressions

<code-block lang="BNF" src="definitions.bnf" include-lines="15,43,44" />

An anonymous function expression defines a function without a name. This expression returns a function object of type `sl.types::function<ReturnType, ...ParameterType[]>` where `ReturnType` is the return type of the function and `ParameterType` are the types of the parameters of the function.

An anonymous function optionally starts with a parameter list enclosed in vertical bars (`|`), followed by a colon and the return type. Mandatory is the function body enclosed in curly braces (`{}`).
The parameter list contains a comma-separated list of parameters. Each parameter consists of a name, followed by a colon and the type of the parameter.
If the parameter list and return type are omitted, the function will have no parameters and a return type of `sl.types::void`.

> Different from function definitions in a type, an anonymous function cannot specify a class reference parameter or variadic parameters.
{style="note" title="Difference to function definitions"}

## 4.6.1 Capturing scope variables

An anonymous function can capture variables from the surrounding scope. The captured variables are passed by reference, that means if the variable is changed in the anonymous function, the change will be visible in the surrounding scope.

**Example:**

```
// Define a function that uses an anonymous function to increment a variable
testFunction: sl.types::function<sl.types::void> := ||: void {
	test: sl.types::number := 10;
	sl::io:out("Before: " + test);
	// Define an anonymous function that captures the variable "test"
	increment: sl.types::function<sl.types::void> :=
		||: void {
			test + 1 -> test;
		};
	increment();
	sl::io:out("After: " + test);
};
testFunction();
```

### 4.6.1.1 Capturing implementation
<primary-label ref="ns"/>

This section contains implementation details that are not part of the language specification.

When an anonymous function is defined, the compiler or interpreter should determine which variables from the surrounding scope are used in the anonymous function. If any are captured create a copy of the `sl.types::function` class with a special field containing all the fields.

Consider that the implementation of the `sl.internal::typeOf` function should return the correct type of the anonymous function and not the internal type created for capturing the variables.

**Example:**
This example uses the normally not valid star character (`*`) in an identifier to illustrate the concept of internal names.
Further we assume that we can inherit from `sl.types::function` which is not possible in Karo normally.
```
sl.types::test {
	#entryPoint; ||: void {
		k: number := 10;
		func: function<void> :=
			||: void {
				k + 1 -> k;
			};
		io:out(k);
		func();
		io:out(k);
		testFunc(func);
	}
	
	testFunc |a: function<void>|: void {
		io:out(a.Name);
	}
}

// Is rewritten to something like this:
sl.types::test {
	#entryPoint; ||: void {
		func: *capturingFunction1 := *internal::*capturingFunctionType1();
		10 -> *capturingFunction1.*k;
		io:out(*capturingFunction1.*k);
		*capturingFunction1();
		io:out(*capturingFunction1.*k);
		testFunc(*capturingFunction1);
	}
	
	testFunc |a: function<void>|: void {
		io:out(a.Name);
	}
}

[inherits<sl.types::function<void>>]
*internal::*capturingFunctionType1 {
	[public]
	*k: number;
	
	[callable]
	[override]
	|self: !|: void {
		self.k + 1 -> self.k;
	};
}
```

```
sl.types::test {
	#entryPoint; ||: void {
		func: function<void> :=
			||: void {
			};
		func2: function<void> :=
			||: void {
				func();
			};
		func2 -> func;
	}
	
	testFunc |a: function<void>|: void {
		io:out(a.Name);
	}
}

// Is rewritten to something like this:
sl.types::test {
	#entryPoint; ||: void {
		func: *capturingFunction1 := *internal::*capturingFunctionType1();
		10 -> *capturingFunction1.*k;
		io:out(*capturingFunction1.*k);
		*capturingFunction1();
		io:out(*capturingFunction1.*k);
		testFunc(*capturingFunction1);
	}
	
	testFunc |a: function<void>|: void {
		io:out(a.Name);
	}
}

[inherits<sl.types::function<void>>]
*internal::*capturingFunctionType1 {
	[public]
	*k: number;
	
	[callable]
	[override]
	|self: !|: void {
	};
}
[inherits<sl.types::function<void>>]
*internal::*capturingFunctionType2 {
	[public]
	*k: number;
	
	[callable]
	[override]
	|self: !|: void {
	};
}

```
