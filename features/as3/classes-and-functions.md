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

# Classes and Functions

Classes and functions in ActionScript 3

## File Structure
As mentioned in [packages](features/as3/packages), each file in ActionScript needs a `package` declaration. Similarly, there must be exactly one file for each externally visible Class (or function). Additionally, the class name must match the class name exactly. By convention, class names start with an uppercase character.

## Inheritance and interfaces
ActionScript classes can only inherit from a single `super` class, but you can declare multiple interfaces. So if you need a class to be more than one unrelated types, you should use interfaces to declare your types rather than classes. Sub-classing and declaring interfaces looks like this:

```
public class SubClass extends SuperClass implements IFoo, IBaz, IBar
```

## Constructors
Constructors in ActionScript are optional. If you need to initialize something in your class you should always declare a constructor and you can define at which point the `super` class is instantiated by calling `super()` inside the constructor. Subclasses and super-classes do not need to have the same number of arguments so the following is perfectly valid:

```
package{
	public class SubClass(){
		foo = "foo";
		super("baz")
	}
	private var foo:String
}
```

## Static accessors
By default
## Using `this`
