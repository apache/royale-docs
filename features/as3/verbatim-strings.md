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
title: Verbatim strings
description: Verbatim strings in ActionScript
permalink: /features/as3/verbatim-strings
---

# Verbatim strings in ActionScript

[Apache Royale](https://royale.apache.org/){:target='_blank'} adds support for declaring _verbatim strings_ in [ActionScript](features/as3). Verbatim strings start with a `@` character and don't treat the `\` character as the start of an escape sequence.

Verbatim strings are also supported by the compiler included with the Adobe AIR SDK starting with version 50.0.

## Code example

Consider the following code that prints a regular string to the debug console:

```as3
var regular:String = "one\ntwo";
trace(regular);
```

In the debug console output, the `\n` sequence within a regular string will be displayed as a new line.

```
one
two
```

The following code prints a verbatim string to the debug console.

```as3
var verbatim:String = @"one\ntwo";
trace(verbatim);
```

In the debug console output, `\` and `n` in a verbatim string are displayed as distinct characters.

```
one\ntwo
```

## Limitations of verbatim strings in Royale

Other ActionScript compilers, such as the one in the [Apache Flex SDK](https://flex.apache.org/){:target='_blank'}, may not recognize verbatim strings. Attemping to pass ActionScript or MXML source code that contains verbatim strings to another compiler may result in compile-time errors. In other words, to write 100% portable ActionScript code that works with any compiler, avoid using verbatim strings and any of Royale's other [extensions to the ActionScript language](features/as3#new-actionscript-language-features-in-royale).
