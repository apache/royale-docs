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
title: Private constructors
description: Private constructors in ActionScript
permalink: /features/as3/private-constructors
---

# Private constructors in ActionScript

-allow-private-constructors

[Apache Royale](https://royale.apache.org/){:target='_blank'} adds support for declaring the constructor of a class `private` instead of `public` in [ActionScript](features/as3). When a constructor is private, it cannot be instantiated with the `new` keyword outside of the class where it is defined. Private constructors are commonly used for implementing the *singleton* design pattern, which is when only one instance of a particular class should ever be created.

_Requires Apache Royale 0.9.6 or newer._

## Compiler option

Royale enables private constructors by default. To disable private constructors in your application, use the `-allow-private-constructors` compiler option.

```sh
mxmlc -allow-private-constructors=false MyApp.mxml
```

## Code example

You might implement a global logger as a singleton by using a private constructor.

```as3
package
{
	public class Logger
	{
		private static var _instance:Logger;

		public static function getInstance():Logger
		{
			if(!_instance)
			{
				_instance = new Logger();
			}
			return _instance;
		}

		private function Logger()
		{
		}

		public function log(message:String):void
		{
			trace("LOG: " + message);
		}
	}
}
```

If you were to attempt to instantate this `Logger` class, the compiler would fail with an error:

```as3
package com.example
{
	public class MyApplication
	{
		public function MyApplication()
		{
			// Error: Attempted access of inaccessible constructor through a reference with static type Logger
			var obj:Logger = new Logger();
		}
	}
}
```

However, you may call `Logger.getInstance()` to access an instance that is created inside the `Logger` class itself:

```as3
package com.example
{
	public class MyApplication
	{
		public function MyApplication()
		{
			Logger.getInstance().log("Application started");
		}
	}
}
```

## Limitations of private constructors in Royale

Checking whether a constructor is private happens at compile-time only. However, by using reflection APIs, a developer could gain access to a private constructor and instantiate it at run-time without errors.

If a SWC library contains classes with private constructors, applications using that library must also enable private constructors before the compiler will enforce any restrictions.

Other ActionScript compilers, such as the one in the [Apache Flex SDK](https://flex.apache.org/){:target='_blank'}, may not recognize or enforce private constructors. Attemping to pass source code or SWC libraries that contain classes with private constructors to another compiler may result in compile-time errors or unexpected behavior at run-time. In other words, to write 100% portable ActionScript code that works with any compiler, you should avoid using private constructors and any of Royale's other [extensions to the ActionScript language](features/as3#new-actionscript-language-features-in-royale).

