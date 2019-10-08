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
title: RoyaleUnit metadata
description: RoyaleUnit metadata tags
permalink: /testing/royaleunit/metadata
---

# RoyaleUnit metadata

Metadata tags for defining unit tests with RoyaleUnit

The following ActionScript metadata tags may be used with RoyaleUnit test classes:

* [After](testing/royaleunit/metadata.html#after)
* [AfterClass](testing/royaleunit/metadata.html#afterclass)
* [Before](testing/royaleunit/metadata.html#before)
* [BeforeClass](testing/royaleunit/metadata.html#beforeclass)
* [Ignore](testing/royaleunit/metadata.html#ignore)
* [RunWith](testing/royaleunit/metadata.html#runwith)
* [Suite](testing/royaleunit/metadata.html#suite)
* [Test](testing/royaleunit/metadata.html#test)

## After

Specify a method to run after each test in this class.

```actionscript
[After]
public static function after():void
{
	// runs after every test method in the same class
}
```

## AfterClass

Specify a static method to run one time, after all tests have completed in this class.

```actionscript
[AfterClass]
public static function afterClass():void
{
	// runs after all test methods in the same class have completed
}
```

> Using `[AfterClass]` metadata requires a nightly build of Apache Royale 0.9.7. This metadata will not work properly in version 0.9.6.

## Before

Specify a method to run before each test in this class.

```actionscript
[Before]
public static function before():void
{
	// runs before every test method in the same class
}
```

## BeforeClass

Specify a static method to run one time, before any tests have run in this class.

```actionscript
[BeforeClass]
public static function beforeClass():void
{
	// runs before all test methods in the same class
}
```

> Using `[BeforeClass]` metadata requires a nightly build of Apache Royale 0.9.7. This metadata will not work properly in version 0.9.6.

## Ignore

Specify that a specific test method should not run.

```actionscript
[Ignore]
[Test]
public function ignoredTest():void
{
	// this test will not be run
}
```

## RunWith

Specify the runner to be used with a specific test suite. Should be combined with [`[Suite]` metadata](testing/royaleunit/metadata.html#suite) metadata.

```actionscript
[Suite]
[RunWith("org.apache.royale.test.runners.SuiteRunner")]
public class MySuite()
{
}
```

In most cases, the runner should be `org.apache.royale.test.runners.SuiteRunner`, but it is possible to create a custom runner, if desired.

## Suite

Specify that a class is a test suite. Should be combined with [`[RunWith]` metadata](testing/royaleunit/metadata.html#runwith).

```actionscript
[Suite]
[RunWith("org.apache.royale.test.runners.SuiteRunner")]
public class MySuite()
{
	public var myTestCase:MyTestCase;
	public var myOtherSuite:MyOtherSuite;
}
```

To add test classes to the suite, define a public variable for each class, using the class as the variable type. You may also add other suite classes in the same way.

## Test

Specify that a method is a test that should be run.

```actionscript
[Test]
public function testSimpleAdd():void
{
	var result:Number = 2 + 3;
	Assert.assertEquals(result, 5);
}
```

### async

To test asynchronous functionality, add the `async` modifier to the `[Test]` metadata, and use the static methods on the `org.apache.royale.test.async.Async` class to set up a context for testing asynchronously.

```actionscript
[Test(async)]
public function testAsync():void
{
	Async.delayCall(this, function():void
	{
		// add asserts here
	}, 250);
}
```

In the example above, we use `Async.delayCall()` to call a function after 250 milliseconds. See the `Async` class for a number of different methods that you can use for asynchronous tests.

> The `async` modifier requires a nightly build of Apache Royale 0.9.7. It is not supported in version 0.9.6.

### timeout

By default, asynchronous tests fail if they do not complete within 500 milliseconds. Set the `timeout` modifier on the `[Test]` metadata to customize this duration (measured in milliseconds).

```actionscript
[Test(async,timeout="2000")]
public function testAsyncWithCustomTimeout():void
{
}
```

> The `timeout` modifier requires a nightly build of Apache Royale 0.9.7. It is not supported in version 0.9.6.

### expected

To require that a specific exception is thrown while a test is running, set the `expected` modifier on the `[Test]` metadata to the name of the exception class.

```actionscript
[Test(expected="RangeError")]
public function testWithExpectedException():void
{
	throw new RangeError("Out of range");
}
```

If the exception class is in a package, include the full package name.

```actionscript
[Test(expected="com.example.CustomError")]
```

> The `expected` modifier requires a nightly build of Apache Royale 0.9.7. It is not supported in version 0.9.6.