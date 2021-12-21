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
Details about strict equality...

## Strings and Numbers
Differences there

## Arrays and Vectors
Link to that page and basic difference...

## XML
Basics about XML and link to that page

## Type casting
Basics about type casting...

## `is` and `as`
Advantages and considerations...

## Kitchen sink
To include or not?

what else....