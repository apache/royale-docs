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
title: Create a unit test
---

# Create a unit test

An example of creating unit tests with RoyaleUnit

## Test cases

A test case is a class that defines a collection of tests. Each test is written as a method of a class. Each test method should be marked with [`[Test]` metadata](testing/royaleunit/metadata.html#test).

```actionscript
package com.example
{
	import org.apache.royale.test.Assert;

	public class MyFirstTests
	{
		[Test]
		public function testSimpleAdd():void
		{
			var result:Number = 2 + 3;
			Assert.assertEquals(result, 5);
		}
		
		[Test]
		public function testSimpleSubtract():void
		{
			var result:Number = 6 - 4;
			Assert.assertEquals(result, 2);
		}
	}
}
```

Each test method should be marked with [`[Test]` metadata](testing/royaleunit/metadata.html#test):

```actionscript
[Test]
public function testSimpleAdd():void
```

The `org.apache.royale.test.Assert` class defines a number of assertion methods that may be useful for testing. In this case, use `assertEquals()` to compare two values:

```actionscript
Assert.assertEquals(result, 5);
```

If the value of the `result` variable is not equal to `5`, the test will fail.

## Run unit tests

Create a simple Apache Royale application and name it *MyTests.mxml*:

```mxml
<?xml version="1.0" encoding="utf-8"?>
<js:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
				xmlns:js="library://ns.apache.org/royale/basic" 
				xmlns:test="org.apache.royale.test.*" 
				applicationComplete="runTests()">
	<fx:Declarations>
		<test:RoyaleUnitCore id="core"/>
	</fx:Declarations>
	<fx:Script>
		<![CDATA[
			import org.apache.royale.test.listeners.TraceListener;
			import com.example.MyFirstTests;
			
			public function runTests():void
			{
				core.addListener(new TraceListener());
				core.runClasses(MyFirstTests);
			}
			
		]]>
	</fx:Script>
	<js:valuesImpl>
		<js:SimpleValuesImpl values="[]"/>
	</js:valuesImpl>
</js:Application>
```

Use an instance of the `RoyaleUnitCore` class to run unit tests:

```mxml
<test:RoyaleUnitCore id="core"/>
```

> Notice the `test` namespace using the `org.apache.royale.test.*` package where the `RoyaleUnitCore` class is defined.

The `TraceListener` class tells `RoyaleUnitCore` displays the test results in the debug console:

```actionscript
core.addListener(new TraceListener());
```

Pass one or more test classes to the `runClasses()` method of the `RoyaleUnitCore` instance:

```actionscript
core.runClasses(MyFirstTests);
```

Compile this application and run it using a debugger to see the results of the tests.

```sh
mxmlc -keep-as3-metadata+=Test MyTests.mxml
```

> Don't forget to tell the compiler to keep any [RoyaleUnit metadata](testing/royaleunit/metadata.html) that is used in the application. In this case, only `[Test]` metadata is used, but several other tags are available.

The debug console output should look similar to the following:

```
com.example::MyFirstTests.testSimpleAdd .
com.example::MyFirstTests.testSimpleSubtract .
Time: 0.346
OK (2 tests)
```