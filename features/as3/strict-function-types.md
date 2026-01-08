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
title: Strict function types
description: Strict function types in ActionScript
permalink: /features/as3/strict-function-types
---

# Strict function types in ActionScript

-strict-function-types

[Apache Royale](https://royale.apache.org/){:target='\_blank'} adds support for strict function types in [ActionScript](features/as3). Sometimes also called _function type expressions_, strict function types allow developers to require a function to have a compatible signature before it can be assigned to a variable, passed as a function parameter, or returned from a method. Strict function types are completely optional, and ActionScript still supports the `Function` type that accepts any function, regardless of signature.

_Requires Apache Royale 0.9.13 or newer._

## Compiler option

Royale enables strict function types by default. To disable strict function types in your application, use the `-strict-function-types` compiler option.

```sh
mxmlc -strict-function-types=false MyApp.mxml
```

## Code examples

Traditionally, to assign a function to a variable in ActionScript, a developer would set the variable's type to `Function`.

```as3
var greet:Function;
greet = function(name:String):String
{
    return "Hello, " + name;
}
var greeting:String = greet("hi");
```

If a developer tries to call the `Function` with incorrect arguments, or assigns the return value to an incompatible type, the compiler will allow it because the signature information has been lost.

```as3
// no errors because the type of greet is Function
var result:Array = greet(123.4, true);
```

A function type expression may be used instead of `Function` to retain the signature so that the compiler may check for errors when the function is called.

```as3
var strictGreet:(s:String)=>String;
strictGreet = function(name:String):String
{
    return "Hello, " + name;
}
var greeting:String = strictGreet("hi");
```

The following attempt to call `strictGreet` will fail because the arguments don't match the parameter types and the return type doesn't match the variable it is assigned to.

```as3
// Error: Implicit coercion of a value of type String to an unrelated type Array.
// Error: Incorrect number of arguments.  Expected no more than 1
// Error: Implicit coercion of a value of type Number to an unrelated type String.
var result:Array = strictGreet(123.4, true);
```

The compiler also checks for errors when a function is assigned to the function type expression. The following assignment fails because the parameter type does not match.

```as3
var strictGreet:(s:String)=>String;

// Error: Implicit coercion of a value of type (n:Number)=>String to an unrelated type (s:String)=>String.
strictGreet = function(n:Number):String
{
    return n.toString();
}
```

The signature of the assigned function does not need to match the function type expression exactly. Its parameter and return types may differ if they are compatible when one is assigned to the other.

For example, if you create a class `B` that extends class `A`, you may assign variables of type `B` to variables of type `A`.

```as3
class A {}
class B extends A {}

var a:A;
var b:B;

a = b; // valid; no error!
```

Inheritance is also considered when checking whether function signatures are compatible.

```as3
var func1:(x:B)=>void;
var func2:(x:A)=>void;
```

When `func1` is called, it will be passed a value of type `B`. `func2` is considered compatible with `func1` because a value of type `B` may be assigned to a parameter of type `A`.

```as3
func1 = func2; // valid; no error!
```

However, `func2` will accept any value of type `A`. If there's another class, `C`, that also extends `A`, but doesn't extend `B`, this value of type `C` cannot be assigned to a parameter of type `B`, so an error must be reported if `func1` is assigned to `func2`.

```as3
// Error: Implicit coercion of a value of type (x:A)=>void to an unrelated type (x:B)=>void.
func2 = func1;
```

A `...rest` parameter is compatible with any number of parameters, and their types don't matter.

```as3
var func1:(x:String, y:Number, z:Boolean)=>void;
var func2:(...rest)=>void;
func1 = func2;
```

`func2` can accept any combination of arguments, including the `String`, `Number`, and `Boolean` that must be passed to `func1`, so `func2` is allowed to be assigned to `func1`.

Inheritance is also considered for return types.

```as3
var func1:()=>A;
var func2:()=>B;
```

When `func1` is called, it will be return a value of type `A`. `func2` is considered compatible with `func1` because it returns a value of type `B`, which is a subclass of `A`.

```as3
func1 = func2; // valid; no error!
```

However, `func1` may return any value of type `A`. If there's another class, `C`, that also extends `A`, but doesn't extend `B`, this value of type `C` would not be a compatible return type for `func2`, so an error must be reported if `func1` is assigned to `func2`.

```as3
// Error: Implicit coercion of a value of type ()=>A to an unrelated type ()=>B.
func2 = func1;
```

A function type expression with a `void` return type is compatible with any other return type because the return type may be safely ignored.

```as3
var func:(x:String)=>void;
function greet(name:String):String
{
    var greeting:String = "Hello, " + name;
    trace(greeting);
    return greeting;
}
func = greet;
```

## Limitations of strict function types in Royale

Other ActionScript compilers, such as the one in the [Apache Flex SDK](https://flex.apache.org/){:target='_blank'}, may not recognize strict function types. Attemping to pass ActionScript or MXML source code that contain strict function types to another compiler may result in compile-time errors. In other words, to write 100% portable ActionScript code that works with any compiler, avoid using arrow functions and any of Royale's other [extensions to the ActionScript language](features/as3#new-actionscript-language-features-in-royale).

Strict function types are a compile-time only feature. At runtime, strict function types are ignored and treated as if the type were simply `Function`. No run-time exception will be thrown if the signature of a function assigned to a variable with a strict function type does not match.
