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
title: ActionScript Packages
description: Packages in ActionScript 3
permalink: /features/as3/packages
---

# ActionScript Packages

Packages in ActionScript 3

Code in ActionScript is structured the same way Java code is structured. Each ActionScript file must declare its package and wrap any externally visible class in the package. A top level package does not need a name. So for a `Foo` class at the top level, it would look like this:

```
package {
	class Foo {
		public function Foo() {
		}
	}
}
```
You can name your folder structure any way you like, but an accepted convention is to nest it in a unique domain to prevent potential package conflicts. So for a class `MyFoo` you might have a folder structure like this: `src/com/acme/MyFoo.as` and the class would look like this:

```
package com.acme {
	class MyFoo {
		public function MyFoo() {
		}
	}
}
```

Always structure your packages, so all classes have a unique qualified path.

[Read more about classes and functions](features/as3/classes-and-functions)