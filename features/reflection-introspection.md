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
title: Reflection and introspection
description: Finding the class and details of an object
permalink: /features/reflection-introspection
---
# Reflection and introspection

Finding the class and details of an object

ActionScript 3.0 supports class reflection and introspection using the following functions in the `flash.utils` package:

- getQualifiedClassName
- getQualifiedSuperclassName
- getDefinitionByName
- describeType

## Reflection

Use reflection to find the class of an object.

### getQualifiedClassName
Pass to `getQualifiedClassName()` a reference to an object, and it returns the object's fully qualified class name:

```
var loader:URLLoader = new URLLoader();
var className:String = getQualifiedClassName(loader);
trace(className); // Displays flash.net::URLLoader
```

### getQualifiedSuperclassName
To retrieve the fully qualified superclass name of an object, use getQualifiedSuperclassName():

```
var loader:URLLoader = new URLLoader();
var className:String = getQualifiedSuperclassName(loader);
trace(className); // Displays flash.events::EventDispatcher
```

### getDefinitionByName

If you have a class or function name, you can retrieve a reference to with `getDefinitionByName()`. Provide a string parameter specifying a fully qualified class or function name and the function and `getDefinitionByName()` returns its Object type.

If you’re retrieving a class reference, you can cast the return value to Class:

```
var classReference:Class = Class(getDefinitionByName("flash.net.URLLoader"));
```

You can then create a new instance:

```
var instance:Object = new classReference();
```

You can also use the return value from `getQualifiedClassName()` or `getQualifiedSuperclassName()` with `getDefinitionByName()`:

```
var loader:URLLoader = new URLLoader();
var className:String = getQualifiedClassName(loader);
var classReference:Class = Class(getDefinitionByName(className));
var instance:Object = new classReference();
```


## Class introspection

Use **describeType()** to return a description of all the events, public properties, and public methods of an object. For example, to get the details of a URLLoader object, you could use a method like this with a reference to the object:

```
var loader:URLLoader = new URLLoader();
var description:XML = describeType(loader);
trace(description);
```

The method returns an XML object that details the class name, superclass, class settings, implemented interfaces, constructor signature, public method signatures, and descriptions of the public properties of the object.
