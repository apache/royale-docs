---
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
# 
# http://www.apache.org/licenses/LICENSE-2.0
# 
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

layout: docpage
title: Type inference
description: Type inference in ActionScript
permalink: /features/as3/type-inference
---

# Type inference in ActionScript

Using the `-infer-types` compiler option

[Apache Royale](https://royale.apache.org/){:target='_blank'} adds support for _type inference_, which enables the ActionScript compiler to automatically fill in missing type declarations on variables, fields, and function returns. The compiler can typically detect an appropriate type based on a variable's initializer or a function's return statements. This feature gives developers the ability to purposefully omit type declarations — which allows them to write less code, while still gaining the performance and productivity benefits of stricter types.

Traditionally, ActionScript has treated the type of a symbol with no explicitly declared type as the _any_ type `*`, and the compiler would emit a warning for the missing type declaration. When type inference is enabled, the compiler will skip the warning if a type other than `*` can be inferred from the initializer or return statements. If the intended type should actually be `*`, an explicit type declaration is encouraged.

## Compiler option

Royale does not enable type inference by default, to avoid potential backwards compatibility issues with existing AS3 code. To enable type inference in your application, use the `-infer-types` compiler option.

```sh
mxmlc -infer-types=true MyApp.mxml
```

## Code examples

The examples below demonstrate how the types of variables, fields, and function returns are automatically detected when type inference is enabled.

### Local variables

The following local variable is typed as `String` because it is initialized with a string value.

```as3
var localStr = "hello";
```

Similarly, the next local variable is typed as `Number` because it is initialized with a numeric value.

```as3
var localNum = 123.4;
```

### Fields

The following member variable is typed as `Boolean` because it is initialized with the value `true`.

```as3
public var memberVar = true;
```

The property defined below includes both getter and setter functions, and they are used to store data in a `private` member variable. The member variable has an inferred type of `String`, which means that the getter return type and setter parameter type are inferred to be of type `String` too. A setter's return type is always inferred as `void`.

```as3
private var _memberProp = "hello";

public function get memberProp() {
	return _memberProp;
}

public function set memberProp(value) {
	_memberProp = value;
}
```

### Functions

The return type of the function below is `Number` because the result of the `return` statement is numeric.

```as3
function add(a:Number, b:Number) {
	return a + b;
}
```

If a function contains no `return` statements, the inferred type is `void`.

```as3
function log(text:String, source:String = null)
{
	if (source)
	{
		trace("[" + source + "] " + text);
	}
	else
	{
		trace(text);
	}
}
```

If a function contains multiple `return` statements, the common base class of all returned values is used as the inferred type. In the following example, let class `B` extend class `A`. The function's return type will b inferred as `A` because that's the common base class between `A` and `B`.

```as3
function getResult(a:A, b:B, preferB:Boolean = true)
{
	if (preferB)
	{
		return b;
	}
	return a;
}
```

Similar to variable types, function parameter types may be inferred from default values. The parameter below is typed as `String`.

```as3
function callback(result = "success"):void
{
}
```

### Special case: null and undefined

If the initializer or return value is `null`, then the `*` type will be inferred because `null` may be used with many types. This will result in the compiler emitting a warning, even when type inference is enabled.

```as3
// Warning: variable 'defaultsToNull' has no type declaration.
var defaultsToNull = null;
```

It is recommended to declare a type when initializing to `null`.

```as3
var defaultsToNull:String = null
```

Similarly, if the initializer or return value is `undefined`, then the `*` type will be infered, and a warning will be reported.

```as3
// Warning: variable 'defaultsToUndefined' has no type declaration.
var defaultsToUndefined = undefined;
```

To use the `*` type without a warning, it should declared explicitly.

```as3
var defaultsToUndefined:* = undefined;
```

### Special case: Number, int, and uint

While the common base class of `Number`, `int`, and `uint` is technically `Object`, ActionScript allows `int` and `uint` values to be assigned to `Number`. As a special case, the common base class for a mix of `Number`, `int`, or `uint` values will be detected as `Number` instead of `Object`.

The return type of the function below is `Number` because the function returns a mix of `Number` or `int` values.

```as3
function round(value:Number) {
	var integer = int(value);
	var difference = value - integer;
	if (difference >= 0.5) {
		return integer + 1.0;
	}
	return integer;
}
```

### Special case: Interfaces

ActionScript allows an [interface](features/as3/interfaces) to extend one or more other interfaces. When inferring the return type of a function, the case of multiple interface inheritance can result in a situation where determining the correct return type to infer from two interfaces becomes ambiguous, if you were to consider common extended interfaces. This is because two interfaces could both extend more than one common interface. With this in mind, finding the common base type between two interfaces considers only those two interfaces, and not any of the other interfaces that they extend.

Consider the following interfaces:

```as3
interface A {}
interface B extends A {}
interface C extends A {}
```

The base interface between `A` and `B` is `A` because `B` extends `A`. However, in the context of type inference, there is no common base interface between `B` and `C` because `B` does not extend `C` and `C` does not extend `B`. Both `B` and `C` extend `A`, but as you'll see in the next example, that's where things can get ambiguous.

Consider the following interfaces:

```as3
interface J {}
interface K {}
interface L extends J, K {}
interface M extends J, K {}
```

Interface `L` extends `J` and `K`, and interface `M` also extends `J` and `K`. If type inference were to find a common base interface between `L` and `M` by checking which interfaces they both extend, should it choose `J` or should it choose `K`? Neither `J` nor `K` takes precedence in any way, so neither is the better option. With that in mind, type inference must fall back to the `*` type, and the developer can explicitly declare a type to prevent a compiler warning.