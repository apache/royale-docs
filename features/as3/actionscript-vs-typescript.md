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
title: ActionScript vs Typescript
description: Differences between ActionScript and Typescript
permalink: /features/as3/actionscript-vs-typescript
---

# ActionScript vs Typescript

Differences between ActionScript and Typescript

*Warning: This document is a work-in-progress/undergoing review.*

## ActionScript has a different goal than Typescript
Typescript [states their goals](https://github.com/Microsoft/TypeScript/wiki/TypeScript-Design-Goals) as providing compile type type safety and conforming to the Javascript spec supporting all features. Typescript does not provide runtime type safety or any tools beyond compile time types.

Royale's goals are different. It provides a complete development environment. That includes the ActionScript language, debugging tools, a complete UI framework and both debug and deployment compiling.

While Royale give very high priority to performance, our philosophy is that besides compile time type safety, runtime type safety is important too. By providing certain runtime guarantees, a certain class of Javascript bugs disappear. (More details to follow...)

## Testing equality
In Javascript, strict equality is recommended (i.e. `===`) instead of "normal" equality (i.e. `==`). That's because Javascript automatically does a type coercion before comparing equality and can cause unexpected results.

Royale generally does not have these problems and bugs caused by using `==` are extremely rare. That's because types are enforced at _runtime_ time and uncertain values are automatically coerced when assigning the values. Normal equality has advantages and can be used for automatically evaluating certain types (such as `XML`). Therefore the general recommendation in ActionScript and Royale is to use `==` instead of `===`.

The exception to this rule is if you are using untyped variables (i.e. `*`) and need to test for `undefined` to the exclusion of `null`. In that case you need `foo.baz === undefined`.

## Strings and Numbers
Strings and numbers in Javascript can either be literal primitives (i.e. `foo`, `3.14`) or classes (i.e. `new String("foo")`, `new Number(3.14)`). These are two distinct types in Javascript and in turn in Typescript. In Typescript, you would declare the former using `string` and `number`, while the latter would be `String` and `Number`. Trying to mix the two in Typescript will cause warnings.

ActionScript does not differentiate between the two types. Both types use the Uppercase notation, so you have `String` and `Number`, but no `string` or `number` `'foo' is String` and `new String("foo") is String` both resolve to true in ActionScript. If you try to use strict equality on the two (i.e. `===`), it will fail, but if you use the standard ActionScript practices, you don't need to worry about whether strings and numbers are literals or not.

## Arrays and Vectors
Typed arrays is an important piece in declaring types. ActionScript does not currently have typed Arrays. All Arrays are untyped with the exception of cases where [implicit coercions are detected](create-an-application/optimizations/compiler-configuration-settings.html#implicit-complex-coercions). For "typed arrays" in ActionScript you use [Vectors](features/as3/vectors). Vectors are similar to Arrays, but have some differences. Vectors has some features which can be enforced at runtime. See the page about [Vectors](features/as3/vectors) for full details.


## XML
Dealing with XML in Javascript is difficult at best. Many people try to bash XML in defence of Javascript's poor XML support. That's not very helpful if you have a legitimate use for XML.

In 2004 and 2005, [Ecma published ECMA-357](https://www.ecma-international.org/publications-and-standards/standards/ecma-357/) which was a spec for handling XML in Javascript. The spec was called E4X (Ecmascript for XML). This was adopted by Firefox and ActionScript. Unfortunately it was not adopted by Chrome, so it never became a Javascript standard. Royale supports the full E4X spec and XML is treated as a first class citizen in Royale. This makes dealing with XML **much** easier. Read the [page on XML](features/as3/xml) for full details.

Royale also has a lightweight [JXON](https://royale.apache.org/asdoc/#!org.apache.royale.utils/JXON) class which can be useful for simple reading of XML if you don't need all the functionality of E4X.

## Interfaces
## Type casting
Basics about type casting...

## `is` and `as`
Advantages and considerations...

## Kitchen sink
To include or not?

what else....