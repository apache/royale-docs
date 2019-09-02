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
title: Abstract classes
description: Abstract classes in ActionScript
permalink: /features/as3/abstract-classes
---

# Abstract classes in ActionScript

-allow-abstract-classes

[Apache Royale](https://royale.apache.org/){:target='_blank'} adds support for declaring `abstract` classes in [ActionScript](features/as3). An abstract class cannot be instantiated using the `new` keyword, meaning that it must be subclassed. Additionally, an abstract class may declare `abstract` methods that do not have a function body. Abstract methods must be implemented by the concrete subclass, similar to how the methods of an interface must also be implemented.

## Enable abstract classes

Like other [new ActionScript language features](features/as3#new-actionscript-language-features-in-royale) that Royale adds, abstract classes are enabled by default. To disable abstract classes in your application, use the `-allow-abstract-classes` compiler option.

```sh
mxmlc -allow-abstract-classes=false MyApp.mxml
```

## Code example

Consider the following code that creates a class named `GraphicsObject`:

```actionscript
package
{
	public abstract class GraphicsObject
	{
		public function GraphicsObject()
		{
		}

		public var x:Number;
		public var y:Number;

		public abstract function draw(context:IGraphicsContext):void;
	}
}
```

This class uses the `abstract` modifier, so if we tried to instantiate the class directly, we'd get a compile-time error:

```actionscript
// Error: Abstract classes cannot be instantiated with the new operator.
var object:GraphicsObject = new GraphicsObject();
```

The `GraphicsObject` class defines a method named `draw()` that also uses the `abstract` modifier. This method does not have a body, and it will need to be implemented in a subclass.

> The `IGraphicsContext` type used by the single parameter of `draw()` is a hypothetical interface that (for the purposes of this example) we'll say has two methods, named `moveTo()` and `lineTo()`.

The next code sample show how to extend the abstract class `GraphicsObject` and implement its `draw()` method:


```actionscript
package
{
	public class Rectangle extends GraphicsObject
	{
		public function Rectangle(width:Number, height:Number)
		{
			this.width = width;
			this.height = height;
		}

		public var width:Number;
		public var height:Number;

		public abstract function draw(context:IGraphicsContext):void
		{
			context.moveTo(x, y);
			context.lineTo(x + width, y);
			context.lineTo(x + width, y + height);
			context.lineTo(x, y + height);
			context.lineTo(x, y);
		}
	}
}
```

If we extended `GraphicsObject` and did not implement its abstract method, we'd get a compile-time error:


```actionscript
package
{
	// Error: Method draw in abstract class GraphicsObject not implemented by class Foobar
	public class Foobar extends GraphicsObject
	{
		public function Foobar()
		{
		}
	}
}
```

## Limitations of abstract classes in Royale

Checking whether a class is abstract happens at compile-time only. However, by using reflection APIs, a developer could potentially gain access to an abstract class and instantiate it at run-time without errors.

If a SWC library contains classes with abstract classes, applications using that library must also enable abstract classes before the compiler will enforce any restrictions.

Other ActionScript compilers, such as the one in the [Apache Flex SDK](https://flex.apache.org/){:target='_blank'}, may not recognize or enforce private constructors. Attemping to pass source code or SWC libraries that contain classes with private constructors to another compiler may result in compile-time errors or unexpected behavior at run-time. In other words, to write 100% portable ActionScript code that works with any compiler, you should avoid using abstract classes and any of Royale's other [extensions to the ActionScript language](features/as3#new-actionscript-language-features-in-royale).
