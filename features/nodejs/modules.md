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

One of the reasons why the [Node.js](features/nodejs) ecosystem is so vibrant is the massive number of open source modules available to install from [the npm registry](https://www.npmjs.com/). Those modules are all deployed as JavaScript, but they can be written in a variety of languages that can compile to JavaScript, including [ActionScript](features/as3) with [Apache Royale](https://royale.apache.org/).

## A simple module

Create a file named *leftPad.as* and add the following code:

```actionscript
package
{
    public function leftPad(input:String, minLength:int, char:String = " "):String
    {
        var result:String = input;
        while(result.length < minLength)
        {
            result = char + result;
        }
        return result;
    }
}
```

This function takes an input string, and if its length is less than the specified minimum, additional characters are appended to to beginning until the result meets the length requirement.

## Compile with asnodec

Using Apache Royale's **asnodec** compiler, compile the project into JavaScript code that can be run with Node.js:


```sh
asnodec -targets=JSNodeModule src/leftPad.as
```

Use the `-targets` compiler option to specify that the output should be a module instead of a [standalone script](features/nodejs/scripting).

## Run the project

To test the module, create a file named *script.js* in the root folder of your project, and add the following content:

```js
var leftPad = require("./bin/js-release/index.js");
var inputString = "64";
var result = leftPad(inputString, 4, "0");
console.log(result);
```

> To run the generated JavaScript, you must have [Node.js](https://nodejs.org/) installed.


Use the following command to run the script:

```sh
node script.js
```

The following output will appear in the console:

```
0064
```

## Deploy the module

To deploy a module to [the npm registry](https://www.npmjs.com/), you must create a *package.json* file.

For a project compiled with Apache Royale, the `main` field should point to the generated JavaScript entry point:

```
{
    "name": "my-left-pad",
    "version": "1.0.0",
    "main": "bin/js-release/index.js"
}
```

> When your package is installed in a user's project, they should call `require()` using the value of `name` field in your module's *package.json*.

For complete details about publishing a package to the npm registry, please see [npm: Packages and modules](https://docs.npmjs.com/packages-and-modules/).