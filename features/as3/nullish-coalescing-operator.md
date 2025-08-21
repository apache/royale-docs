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
title: Nullish coalescing operator
description: Nullish coalescing operator in ActionScript
permalink: /features/as3/nullish-coalescing-operator
---

# Nullish coalescing operator in ActionScript

[Apache Royale](https://royale.apache.org/){:target='\_blank'} adds support for the _nullish coalescing operator_ in [ActionScript](features/as3), which uses the symbol `??`. The `??` operator accepts two operands, one each on its left and right sides. Which operand is returned depends on whether the left operand is _nullish_ or not.

Nullish values include `null` and `undefined` only. If the left operand is not nullish, then it is returned immediately, without executing the right operand. If the left operand is nullish, then the right operand is returned instead.

The nullish coalescing operator is also supported by the compiler included with the Adobe AIR SDK starting with version 50.0.

## Code example

Consider the following code that uses the `??` operator to provide a non-null value if the left operand is nullish.

```as3
var obj:Object = null;
trace(obj == null); // true
var resolved:Object = obj ?? {};
trace(obj == null); // false
```

The next code shows that the left operand will be returned when it is not nullish.

```as3
var obj:Object = {};
var resolved:Object = obj ?? {};
trace(resolved == obj); // true
```

The code below demonstrates the difference between `??` and `||` when encountering a _falsy_ value.

```as3
var num:Number = 0;
var checkNullish:Number = num ?? -1;
var checkFalsy:Number = num || -1;
trace(checkNullish == -1); // false
trace(checkFalsy == -1); // true
```

## Limitations of the nullish coalescing operator in Royale

Other ActionScript compilers, such as the one in the [Apache Flex SDK](https://flex.apache.org/){:target='_blank'}, may not recognize the nullish coalescing operator. Attemping to pass ActionScript or MXML source code that contains nullish coalescing operators to another compiler may result in compile-time errors. In other words, to write 100% portable ActionScript code that works with any compiler, avoid using nullish coalescing operator and any of Royale's other [extensions to the ActionScript language](features/as3#new-actionscript-language-features-in-royale).
