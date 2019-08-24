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
description: 
---
# Circular dependencies



In software, a circular dependency is a relation between two or more classes which either directly or indirectly depend on each other to function properly. An extreme example, which could not work, is:

```as3
public class A extends B

public class B extends A
```

Circular dependencies cause a tight coupling of what should be independent classes. This makes it difficult to re-use one class without its partner. When a developer makes a small change in one of the co-dependent classes, there may be unexpected effects on the other class, leading to poor application behavior or compile-time errors. in the worst case, a circular dependency can generate an infinite recursion leading to a crash or hanging the system.

## What compiling for Flash allows

You can get away with some circular dependencies when developing an application in Flex or Royale that will be compiled for use in Flash or the AIR environment. You can write code like this:

```as3
public class Child {
  public var parent:Parent;
}

public class Parent {
  public var child:Child;
}
```
In Flash and AIR the runtime constructs both classes before type-checking for parent and child properties. Type-checking happens only when the application code has initialized and starts to run.

## What compiling for JavaScript in Royale requires

Royale uses the <a href="https://developers.google.com/closure/compiler/" target="_blank">Google Closure Compiler</a> (GCC) to compile your application into JavaScript that can run on browsers and mobile phones without heavy plugins like Flash. GCC "parses your JavaScript, analyzes it, removes dead code and rewrites and minimizes what's left. It also checks syntax, variable references, and types, and warns about common JavaScript pitfalls." 

GCC does not like circular dependencies that Flash allows. The reason is that, in development mode, each class is loaded by a separate script element, so there has to be a well-defined order to load these scripts. GCC also wants each class to declare the classes it uses via an API called goog.require. So in the Flash example above, Child will have goog.require('Parent') and Parent will have goog.require('Child') and GCC doesn't know which file to load first and it doesn't really want to examine the rest of the file to determine the order.

Fortunately, the Royale compiler has an option called -remove-circulars that is on by default. It analyzes the code and determines which goog.require to remove so GCC won't complain about the circularities and can load the scripts in the right order. However, if you want to know how to refactor your code so that you don't create what GCC considers to be circular dependencies, read on.

GCC recommends refactoring interdependent classes to use interfaces. Some folks believe that classes should never reference other classes, only interfaces. There are some advantages to this approach, but it is more work.

You would define two interfaces like this:

```as3
public class IChild {
}

public class IParent {
}
```

Note that neither interfaces states that the implementation must reference the other interface, otherwise you would have a circularity in the interfaces. You could have implementations reference each other if writing JavaScript yourself because GCC allows more than one top-level 'class' definition in a .js file, whereas ActionScript does not.

Anyway, with these interfaces, the classes look like:


```as3
public class Child implements IChild {
  public var parent:IParent;
}

public class Parent implements IParent {
  public var child:IChild;
}
```
