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
title: Create a Node.js module
description: Write Node.js modules with ActionScript and Apache Royale that can be loaded with require()
permalink: /features/nodejs/modules
---

# Create a Node.js module with Apache Royale

Write modules with ActionScript that can be loaded with `require()` in Node.js

One of the reasons why the [Node.js](features/nodejs) ecosystem is so vibrant is the massive number of open source modules available to install from [npm](https://www.npmjs.com/). Those modules are all deployed as JavaScript, but they can be written in a variety of languages that can compile to JavaScript, including [ActionScript](features/as3).

## Compile with asnodec

Using Apache Royale's **asnodec** compiler, compile our project into JavaScript that can be run with Node.js.


```sh
asnodec -targets=JSNodeModule src/MyModule.as
```

Use the `-targets` compiler option to specify that the output should be a module instead of a [standalone script](features/nodejs/scripting).