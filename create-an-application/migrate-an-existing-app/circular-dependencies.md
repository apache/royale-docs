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
Circular dependencies cause a tight coupling of what should be independent modules. THis makes it difficult to re-use one module without its partner. When a developer makes a small change in one of the co-dependent modules, there may be unexpected effects on the other modules, leading to poor application behavior or compile-time errors. in the worst case, a circular dependency cand generate an infinite recursion leading to a crash or hanging the system.

## What Flex allows

*This material will be available soon.*

## What compiling for JavaScript requires

*This material will be available soon.*
