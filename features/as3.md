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
title: ActionScript 3 (AS3)
description: The object-oriented programming language
permalink: /features/as3
---

# ActionScript 3 (AS3)

The object-oriented programming language

ActionScript 3 is an object-oriented programming language originally created by Macromedia Inc., which continued to evolve after being acquired by Adobe Systems. It is a superset of the ECMAScript standard (more widely known as JavaScript) with a stronger focus on classes, interfaces, and objects. While originally designed for Adobe Flash Player, ActionScript 3 may be used by developers today to build plugin-free, cross-platform, web applications with [Apache Royale](http://royale.apache.org/){:target='_blank'}.

The following code snippet shows some of ActionScript's core syntax:

```as3
package org.apache.royale
{
	public class WelcomeToActionScript
	{
		public function WelcomeToActionScript()
		{
			var message:String = "Hello world";
			sayHi(message, 3);
		}

		private function sayHi(message:String, times:int):void
		{
			for (var i:int = 0; i < times; i++)
			{
				// prints message to debug console
				trace(message);
			}
		}
	}
}
```

## Sections

This document is divided into several sections:

[Metadata](features/as3/metadata) describe the Metadata decorations that can be used for variables and functions.
[Code Conventions](features/as3/code-conventions) explains the typical ways Royale developers name files, classes, function, variables and more.

## New ActionScript language features in Royale

The Royale compiler extends the ActionScript language with useful, new features. These language extensions are considered optional, and to use the new syntax, you must enable certain compiler flags.

The following new ActionScript features are available with the Royale compiler:

* [Abstract Classes](features/as3/abstract-classes)
* [Import Aliases](features/as3/import-aliases)
* [Null Conditional Operator](features/as3/null-conditional-operator)
* [Nullish Coalescing Operator](features/as3/nullish-coalescing-operator)
* [Private Constructors](features/as3/private-constructors)
* [Type Inference](features/as3/type-inference)
* [Verbatim Strings](features/as3/verbatim-strings)

### Limitations of ActionScript language extensions

Other ActionScript compilers, such as the one in the [Apache Flex SDK](https://flex.apache.org/){:target='_blank'}, may not support Apache Royale's extensions to the ActionScript language. Attemping to pass source code or SWC libraries using these language extensions to another compiler may result in compile-time errors or unexpected behavior at run-time. In other words, to write 100% portable ActionScript code that works with any compiler, you should avoid using any of Royale's extensions.