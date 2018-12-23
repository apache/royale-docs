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
title: Calling to/from External JavaScript
---

# Calling to/from External JavaScript

In Flash, there is a class,
<A HREF="https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/external/ExternalInterface.html" target="_blank">ExternalInterface</A>,
that lets your Flex (or Flash) application call other JavaScript code that has been embedded on the hosting web page,
and lets external JavaScript code call a function within the Flex application. When you port a Flex application to Royale,
you may need to replicate this functionality.

To make this easier, there is an implementation of the same API available as
<A HREF="https://github.com/apache/royale-asjs/blob/develop/frameworks/projects/MXRoyale/src/main/royale/mx/external/ExternalInterface.as" target="_blank">mx.external.ExternalInterface</A>.
You should be able to just rename your imports from `flash.external.ExternalInterface` to `mx.external.ExternalInterface`.

For new code, it would be preferable to create an ActionScript wrapper API into the required JavaScript.
This allows you to define a typed interface and the compiler would then pick up any issues around incompatible types
or incorrectly spelled function names. This could allow a line such as:
```
ExternalInterface.call("MyFunction", "value", 123);
```
to be replaced by
```
MyJSInterface.MyFunction("value", 123);
```
ensuring that you haven't misspelled "MyFunction" and that the function is being passed the correct number and types of arguments.

The implementation of your API wrapper class is where you would call the JavaScript functionality directly, which could be simply via reflection:
```
public static function MyFunction(param : String, val : uint) : void
{
  window["myFunction"](param, val);
}
```
It should be possible to make the call to `myFunction` directly, but we may need asdoc decoration to avoid the 'unknown function' error.

For JavaScript to call into a Royale application, we need a listener or callback of some kind to be set up from the Royale application
(particularly if we want to have some context retained). This can be an extension of our existing class, `MyJSInterface`, where we register the callback:
```
public static function RegisterCallback(fncName : String, fncClosure : Function) : void
{
  MyJSInterface[fncName] = fncClosure;
}
```
When we add our callback (e.g. `MyJSInterface.RegisterCallback("testFunction", TestFunc);`)
the Royale compiler creates a method closure that contains the context from where this registration call is made. This lets you access variables - particularly the "this" variable - within the TestFunc method during the callback.

The JavaScript code then can access this via the Royale-generated JavaScript for MyJSInterface:
```
MyJSInterface.testFunction("This will be passed to TestFunc");
```

