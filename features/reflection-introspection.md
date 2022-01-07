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

Reflection and introspection are in the Royale `Reflection` library.

Royale supports class reflection and introspection using the following functions in the `org.apache.royale.reflection` package:

- registerClassAlias
- getAliasByClass
- getClassByAlias
- getAncestry
- getClosureQualifiedName
- getQualifiedClassName
- getQualifiedSuperclassName
- getDefinitionByName
- getDynamicFields
- isDynamicObject
- describeType

## Reflection

Use reflection to find the class of an object.

### registerClassAlias
Sets up an alias mapping for serialization/deserialization purposes. The Royale compiler can auto-generate this when using class level metadata, e.g. [RemoteClass(alias='someAlias')]

```
registerClassAlias("someAlias", com.acme.Foo);
```

### getAliasByClass

Retrieves an alias for a class, based on an alias mapping previously registered with `registerClassAlias`, or possibly using [RemoteClass(alias='someAlias')] metadata.

```
var alias:String = getAliasByClass(com.acme.Foo);
trace(alias); // Displays the alias name (i.e. someAlias)
```

### getClassByAlias
Retrieves a class based on an alias mapping previously registered with `registerClassAlias`, or possibly using [RemoteClass(alias='someAlias')] metadata.

```
var classRef:Class = getClassByAlias("someAlias");
trace(classRef); // Displays the class (i.e. com.acme.Foo)
```

### getAncestry
A utility function to return ancestry (base classes) as a set of qualified names.

```
var ancestry:Array = getAncestry(org.apache.royale.core.UIBase);
trace(ancestry.join(\n))// will output a list of the inheritance tree
```

### getClosureQualifiedName
Returns the qualified name of a closure instance. We recommend comparing against this when checking for closures. It could insulate against future changes or future variation between targets.

(An app developer does not generally use this.)

```
trace(getClosureQualifiedName());// outputs "builtin.as$0.MethodClosure"
```

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

### hasDefinitionWithName
Checks if a name is defined and will return a valid result when calling `getDefinitionByName`.

### getDefinitionByName

If you have a class or function name, you can retrieve a reference to it with `getDefinitionByName()`. Provide a string parameter specifying a fully qualified class or function name and the function and `getDefinitionByName()` returns its Object type.

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

### getDynamicFields
A utility method to check if an object is dynamic (i.e. can have non-sealed members added or deleted).

Note that static class objects are always dynamic, as are (static) Interface Objects.

The function can take four parameters:

1. The class or instance to check for dynamic fields.
2. An optional function which takes a single String argument and returns `true` to include that specific field in the results. If it returns `false`, that property is excluded. Defaults to `null`, which applies no filtering and returns all detected properties.
3. An optional Boolean to verify that the inspect parameter is dynamic before inspecting it for dynamic properties. This should normally be left at its default value of `true`. If it is known that the object is dynamic before calling this method, setting this to `false` could improve performance. The results of calling this method on non-dynamic objects may be less reliable or less consistent across target platforms if checkFirst is false.
4. A Boolean. If `true`, numeric fields will be returned as numeric values.

It returns the dynamic fields as Strings in an Array.

### isDynamicObject
A utility method to check if an object is dynamic (can have non-sealed members added or deleted).

Note that static class objects are always dynamic, as are Interface Objects

```
if(isDynamicObject(myObject)){
	trace("yay!);
}
```

## Class introspection

Use **describeType()** to return a description of all the events, public properties, and public methods of an object. For example, to get the details of a URLLoader object, you could use a method like this with a reference to the object:

```
var loader:URLLoader = new URLLoader();
var description:XML = describeType(loader);
trace(description);
```

The method returns an XML object that details the class name, superclass, class settings, implemented interfaces, constructor signature, public method signatures, and descriptions of the public properties of the object.
