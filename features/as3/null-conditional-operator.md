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
title: Null conditional operator
description: Null conditional operator in ActionScript
permalink: /features/as3/null-conditional-operator
---

# Null conditional operator in ActionScript

[Apache Royale](https://royale.apache.org/){:target='\_blank'} adds support for the _null conditional operator_ in [ActionScript](features/as3), which uses the symbol `?.`. The expression `a?.b` works similarly to a member access expression, like `a.b`. The difference when using `?.` is that, if the left operand is _nullish_, it will immediately return `null` instead of trying to access the right operand and throwing an exception.

The null conditional operator is also supported by the compiler included with the Adobe AIR SDK starting with version 50.0.

## Code example

Consider the following code that uses the `?.` operator to access the field `a` on the condition that the object is not nullish.

```as3
var obj:Object = null;
var resolved:Object = obj?.a;
trace(resolved); // null
```

If the expression `obj.a` were used instead of `obj?.a`, then an exception would be thrown instead.

If the object is not nullish, then it works similarly to regular member access.

```as3
var obj:Object = {a: 123.4};
var resolved:Object = obj?.a;
trace(resolved); // 123.4
```

## Limitations of the null conditional operator in Royale

Other ActionScript compilers, such as the one in the [Apache Flex SDK](https://flex.apache.org/){:target='_blank'}, may not recognize the null conditional operator. Attemping to pass ActionScript or MXML source code that contains null conditional operators to another compiler may result in compile-time errors. In other words, to write 100% portable ActionScript code that works with any compiler, avoid using null conditional operator and any of Royale's other [extensions to the ActionScript language](features/as3#new-actionscript-language-features-in-royale).
