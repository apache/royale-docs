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
title: Language Basics
description: Language basics in ActionScript 3
permalink: /features/as3/language-basics
---

# Language Basics

Language basics in ActionScript 3

ActionScript is a superset of the ECMAScript edition 4 specification. That gives it the same roots as JavaScript and code will look very similar. The biggest difference is the optionally typed quality of ActionScript, and classes. ECMAScript 6 added classes to JavaScript as well, but JavaScript classes are less structured that ActionScript classes.

Because ActionScript was forked from the ECMAScript specification at version 4, there are features that JavaScript has which are missing from ActionScript and vice versa. Below is an overview of the main ActionScript features.

## Scope

There are four levels of access scope in ActionScript:
1. public
2. private
3. protected
4. internal

These are defined by declaring an access modifier before a declaration.

More details to fill in...

## Accessor Types
There are three basic accessor types in ActionScript
1. function
2. var
3. const

ActionScript does not support arrow functions or `let`. The use of the three accessor types are similar to JavaScript.

## Instance and Class Accessors
By default any accessors of a class are instance accessors. For class-level methods, vars and const, you need to add the `static` modifier. For more details [read about static accessors in classes](features/as3/classes-and-functions#static-accessors).

## Primitive Types
TODO

## XML Types
TODO

## Vector Types
TODO

## Type Casting
There's two ways to do type casting: `Foo(myInstance)` and `fooInstance as Foo`. There is a noteworthy difference between these two: `Foo(myInstance)` will throw an error if th type cannot be cast, while `fooInstance as Foo` will assign `null` if it cannot be cast without throwing an error. Runtime type checking can be turned off in the compiler. (add details)

TODO what else belongs here?