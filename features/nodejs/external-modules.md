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
title: Load external Node.js modules
description: Require Node.js modules installed from npm in ActionScript and Apache Royale
permalink: /features/nodejs/external-modules
---

# Load external Node.js modules with Apache Royale

Expose Node.js modules installed from npm to ActionScript

By creating [type definitions](features/externs) with special metadata, developers can use [Node.js](features/nodejs) modules from [ActionScript](features/as3) code.

Let's try to use the [boxen](https://www.npmjs.com/package/boxen) module from [npm](https://www.npmjs.com/) in ActionScript. This module draws a box around a string to display in the console, and it exposes many styling options like colors, padding, and alignment.

First, make sure to install the boxen module in your project's root folder:

```sh
npm install boxen
```

> To install a module from npm, you must have [Node.js](https://nodejs.org/) installed.

## Define the module's API in ActionScript

Create a file named *boxen.as* and add the following code:

```actionscript
package
{
	/**
	 * @externs
	 */
	[JSModule(name="boxen")]
	public native function boxen(message:String, options:Object = null):String;
}
```

This file will tell the Apache Royale compiler how to access the "boxen" module in the generated JavaScript. Let's look in more detail at each part of this file.

All type definitions must include the `@externs` asdoc tag.


```actionscript
/**
 * @externs
 */
```

Additionally, type definitions for Node.js modules must include `[JSModule]` metadata.

```actionscript
[JSModule(name="boxen")]
```

Set the `name` field inside `[JSModule]` to the string that should be passed to a `require()` call in JavaScript to load the module.

The default export of a module should either be a class, a function, or a variable. In this case, the default export of the "boxen" module is a function.

```actionscript
public native function boxen(message:String, options:Object = null):String;
```

The name of the default export should be derived from the name of the module. In this case, the name of the module and the name of the `function` are both `boxen`.

> If the module name contains dashes, the symbol name should be converted to [camel case](https://en.wikipedia.org/wiki/Camel_case). For example, `[JSModule(name="my-example-module")]` would require the symbol to be named `myExampleModule`.

By specifying that the function is `native`, no body is required.

## Use a Node.js module in ActionScript

Create a file named *MyScript.as*, and add the following content:

```actionscript
package
{
	public class MyScript
	{
		public function MyScript()
		{
			var result:String = boxen("I loaded a module!");
			trace(result);
		}
	}
}
```

This simple script passes a string to `boxen()`, and then it writes the result to the console.

## Compile with asnodec

Using Apache Royale's **asnodec** compiler, compile the project into JavaScript code that can be run with Node.js:

```sh
asnodec MyScript.as
```

The generated JavaScript code will be created in the *bin/js-debug* folder for debug builds, and the *bin/js-release* folder for release builds.

## Run the project

> To run the generated JavaScript, you must have [Node.js](https://nodejs.org/) installed.

Use the following command to run the compiled project:

```sh
node bin/js-release/index.js
```

The following output will appear in the console:

```
┌────────────────────────┐
│                        │
│   I loaded a module!   │
│                        │
└────────────────────────┘
```