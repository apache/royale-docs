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
title: Circular dependencies
---
# Circular dependencies

In software, a circular dependency is a relation between two or more modules which either directly or indirectly depend on each other to function properly. An extreme example, which could not work, is:

```
public class A extends B

public class B extends A
```
Circular dependencies cause a tight coupling of what should be independent modules. This makes it difficult to re-use one module without its partner. When a developer makes a small change in one of the co-dependent modules, there may be unexpected effects on the other module, leading to poor application behavior or compile-time errors. in the worst case, a circular dependency can generate an infinite recursion leading to a crash or hanging the system.

## What compiling for Flash allows

You can get away with some circular dependencies when developing an application in Flex or Royale that will be compiled for use in Flash or the AIR environment. You can write code like this:

```
public class Child {
  public var parent:Parent;
}

public class Parent {
  public var child:Child;
}
```
In Flash and AIR the runtime constructs both classes before type-checking for parent and child properties. That happens only when the application code has initialized and starts to run.

## What compiling for JavaScript requires

Royale uses the <a href="https://developers.google.com/closure/compiler/" target="_blank">Google Closure Compiler</a> (GCC) to compile your application into JavaScript that can run on browsers and mobile phones without heavy plugins like Flash. GCC "parses your JavaScript, analyzes it, removes dead code and rewrites and minimizes what's left. It also checks syntax, variable references, and types, and warns about common JavaScript pitfalls." 


*This material will be available soon.*
