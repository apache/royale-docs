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
title: Classes and Functions
description: Classes and functions in ActionScript 3
permalink: /features/as3/classes-and-functions
---

# Classes and functions

Classes and functions in ActionScript 3

## File structure
As mentioned in [packages](features/as3/packages), each file in ActionScript needs a `package` declaration. Similarly, there must be exactly one file for each externally visible Class (or function). Additionally, the class name must match the class name exactly. By convention, class names start with an uppercase character.

## Inheritance and interfaces
ActionScript classes can only inherit from a single `super` class, but you can declare multiple interfaces. So if you need a class to be more than one unrelated types, you should use [interfaces](features/as3/interfaces) to declare your types rather than classes. Interfaces is very often a better design choice that classes for types either way. Sub-classing and declaring interfaces looks like this:

```as3
public class SubClass extends SuperClass implements IFoo, IBaz, IBar
```

## Constructors
Constructors in ActionScript are optional. If you need to initialize something in your class you should always declare a constructor and you can define at which point the `super` class is instantiated by calling `super()` inside the constructor. Subclasses and super-classes do not need to have the same number of arguments so the following is perfectly valid:

```as3
package {
	public class SubClass() {
		foo = "foo";
		super("baz")
	}
	private var foo:String
}
```

## Static accessors {#static-accessors}
By default any accessors of a class are instance accessors. For class-level methods, vars and const, you need to add the `static` modifier. The order of the modifiers do not matter, so `public static var` is the same as `static public var`.

Class accessors are not inherited by their subclasses.

Instance and class accessors must have unique names, so you cannot have both `public var foo` and `public static var foo`.

## Using `this`
Using `this` is usually optional in ActionScript. If there is no local variable (or function) of the specified name, an instance accessor will be used. The only time you will need `this` is when you have a local variable or function and an instance variable or method of the same name.

## Using static accessors
Similarly, static accessors and methods can be referenced without using the class name, so `baz()` will be resolved to `Foo.baz()` automatically. If you are using a public static method (or accessor) outside the class that you will need to explicitly call `Foo.baz()`.

## Using `this` inside functions
A common problem in Javascript is that `this` is lost within functions. ActionScript does not have this issue. You can freely use `this` inside instance methods. If the function is used as a callback, the compiler will automatically wrap the function to resolve `this` at runtime.

In Royale, it's generally not recommended to use `this` inside non-instance methods and functions. In fact that compiler will warn you by default if you do. Generally, the only case where it's necessary to use `this` inside a function in Royale is if you need `Object.defineProperty` for some reason, and even that should be very rare. The `org.apache.royale.utils.object` package has a number of utility functions for helping to define properties without using `this`. Namely: `defineGetter`, `defineProperty`, `defineSimpleGetter` and `defineSimpleProperty`. If you do find yourself looking to use these functions often, you should probably examine your architecture because there's almost guaranteed to be a better way of designing the architecture in Royale.

## Package level functions
You don't need to declare a class to use code. You can have "utility" functions as first class citizens. To create a public function you create a file similar to a class (but name it camel-case). Assuming your file structure is like so: `src/com/acme/doAwesome.as` Inside the file you declare the function like this:

```as3
package com.acme {
	public function doAwesome(notSoAwesome:Object):Awesome {
		return new Awesome(
			doSomethingComplicatedInTheSamePackage(notSoAwesome)
		);
	}
}
```

Then `doAwesome()` is available anywhere in your project. Your IDE should `import com.acme.doAwesome` if you use it.

## Static classes and singletons
One of the cool new features in ActionScript is [private constructors](features/as3/private-constructors). Use that if you have a class that you want to use as static-only class or as a [Singleton](https://en.wikipedia.org/wiki/Singleton_pattern)

## Instance, static and utility functions
The question is then when to use which.
- For OOP programming, you generally want to use instantiated classes.
- Static-only classes are useful for keeping state -- especially when using simple data types.
- Singletons are useful for keeping state when you need finer control over instantiation and/or the data types are more complex.
- When you are not keeping state, utility functions are generally a better choice. They are easier to unit test. They lend themselves more to functional programming, and they generally carry less excess weight associated with classes.