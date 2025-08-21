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
title: Interfaces
description: Interfaces in ActionScript 3
permalink: /features/as3/interfaces
---

# Interfaces

Interfaces in ActionScript 3

## What are interfaces?
Interfaces is one of the core types in ActionScript. An interface is used to define a type of an object independent of the implementation. While classes are where you implement a type, interfaces are where you *declare* the type. Classes must have function bodies, and interfaces *cannot* have function bodies.

Interfaces *do not* have to declare anything. You can declare an interface type which does not require any implementation. This is useful if you want to declare a group of classes belong to a specific type or groups of type. You can even use use `myInstance is IFoo` at runtime to check types. This type check is completely implementation independent.

## What can you declare in interfaces?
Interfaces do not define *scope*. You don't declare something public. Also, interfaces are only for *methods*. You cannot declare variables in an interface. You *can* (and should) declare getter and/or setters in interfaces, but those must be implemented in your classes as getter and setter functions and not vars.

Interfaces *must* be implemented as classes. You cannot declare an interface for a plain JavaScript object like you can in [Typescript](https://www.typescriptlang.org/docs/handbook/2/objects.html).

(Almost) never reference classes in an interface. If the interface needs to accept or return a type, use an interface. Pretty much the only exception to this rule is for native types such as `String`, `Number`, `int`, `XML`, etc.

## What does an interface look like?

Here's one example

```as3
package com.acme {
	public interface IFoo {
		function get name():String;
		function set name(name:String):void;
		function sayFoo(output:IOutput):void;
	}
}
```