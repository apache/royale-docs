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
title: Compiler configuration settings
description: Compiler configuration settings
permalink: /create-an-application/optimizations/compiler-configuration-settings
---
  
# Compiler configuration settings  

Optimization options

This page explains optimizations for JavaScript output that you can use when configuring the [Apache Royale](https://royale.apache.org/) compiler directly. Often these settings involve removing some JavaScript emulations of runtime type-safety that are present in AVM. This can help to improve application performance and/or reduce the size of your final application build.

It can be useful to develop your application with these settings 'on' and then consider switching them to 'off' for your release build, when you have assured yourself it is safe to do so.

You can provide these settings\ on the command line or via royale-config.xml, or via the `additionalOptions` tag for the compiler in maven's `pom.xml`.  

## Available Options:

- [Initialization of default values](create-an-application/optimizations/compiler-configuration-settings.html#default-initializers)
- [Implict Coercions of non-primitive types](create-an-application/optimizations/compiler-configuration-settings.html#implicit-complex-coercions)
- [Parity for strict equality comparisons](create-an-application/optimizations/compiler-configuration-settings.html#strict-equality-comparisons)
- [Vector Index Checking](create-an-application/optimizations/compiler-configuration-settings.html#vector-index-checking)
- [Dynamic access unknown members](create-an-application/optimizations/compiler-configuration-settings.html#dynamic-access-unknown-members)

## Definitions:  

**AVM:** Actionscript Virtual Machine. You can also broadly interpret this to mean 'SWF at runtime', the 'flash player' or 'Adobe AIR runtime'.

## Default initializers {#default-initializers}  

**-js-default-initializers**

Defaults to true. Corresponds to AVM runtime implicit type intialization values, in particular for primitive types.  
Note that some reflection utility functions require this to be true in order for them to work correctly in javascript.  

_Todo: This content is yet to be created_

## Implict Coercions of non-primitive types {#implicit-complex-coercions}  

**-js-complex-implicit-coercions**

Defaults to true. This corresponds to AVM runtime implicit type coercions for non-primitive types (anything that is not a Number, int, uint, String, Boolean) and is not being cast to something that is untyped (__*__ type) or loosely typed, e.g. of **Object** type.  

An (overly simplistic) example would be:

```as3
var cat:Cat = new Cat();
var myCats:Array = [cat]; 
//from this point on, array access of index 0 in myCats 
//represents an unknown type (from the compiler's perspective)
//in AVM, the following would always cause a runtime error
//unless Cat was a subclass of Dog, which we will assume it is not! 
var dog:Dog = myCats[0]; 
```

With true (the default setting), the above example will behave the same in javascript at runtime as it would in AVM. However supporting this runtime behavior does generate extra type-checking code to achieve that result.

In most cases this extra code can be eliminated in the output after the application has been validated to be error-free at runtime. There may however be cases with legacy actionscript that depend on error-handling for these situations and where refactoring that aspect is not a priority. In these cases it can be left on in the release build, or there is also the option to switch it off in general but force it to remain on for specific code scope, for example, using [@royalesuppresscompleximplicitcoercion](create-an-application/optimizations/doc-comment-directives.html#royalesuppresscompleximplicitcoercion).  

Does this feature always catch implicit complex coercions? No, currently there can still be cases which are missing this level of runtime type safety. Notably this can occur in the processing of MXML instances or [data binding](features/data-binding) support.

**Pro tip:** How do I know how much of my code is being affected by this setting? In the javascript **js&#x2011;debug** output, you can do a ***search in files*** for the string **/* implicit cast */** which precedes the compiler-generated code the to support this parity with AVM. That will show you all the sites where it is being output. As with all other code, this can be minimized in the js-release output, but as mentioned earlier, if the application does not have runtime errors, then the performance of the application could be optimized by eliminating these checks.  

## Parity for strict equality comparisons {#strict-equality-comparisons}

**-js-resolve-uncertain**

This is a relatively rare as3 language parity feature that is applied by the compiler when instantiating an unknown class.  
It ensures greater compatibility between AVM and javascript, in particular for strict equality comparisons.  
This is not just important for the binary operators like `===` or `!==`, but also for things like `Array.indexOf`, which uses strict equality for checking.  

An (overly simplistic) example would be:

```as3
var clazz:Class = String;
var test:Array = ['test', new clazz(30.5)]; 
//in AVM, the above would result in: ['test', '30.5']
var idx:int = test.indexOf('30.5');
//with js-resolve-uncertain=true idx will be 1 above (correct)
//in javscript, with js-resolve-uncertain=false, it would be -1 (incorrect)
```

In most cases this setting is probably not going to cause performance issues. But it does add a small amount of extra overhead in both size and performance.

The main variations to cover are the primitive types: **Number**, **String**, **Boolean** etc., as well as synthetic types for **int** and **uint**.

So it can be switched off if after testing it is deemed safe to do so.    
Or it can be specifically avoided or explicitly switched on in specific areas of code with [@royalesuppressresolveuncertain](create-an-application/optimizations/doc-comment-directives.html#royalesuppressresolveuncertain).

**Pro tip:** How do I know how much of my code is being affected by this setting?  
In javascript the **js&#x2011;debug** output, you can do a ***search in files*** for the string **Language.resolveUncertain**   

## Vector index checking {#vector-index-checking}

**-js-vector-index-checks**

Defaults to true. This corresponds to AVM runtime checking during Vector index assignments (*note:* currently only for assignment, not access)  

An (overly simplistic) example would be:

```as3
var myVec:Vector.<Number> = new Vector.<Number>();
myVec[1] = 2; 
//the above will generate a runtime error in AVM,
//because Vectors must have contiguous index ranges. 
//In this case the length is zero, and the first assignment 
//can only be made to index 0, not index 1.
```

or:

```as3
myVec = new Vector.<Number>(20,true); //create a fixed length Vector, with indices 0 to 19.
myVec[20] = 2; 
//the above will generate a runtime error in AVM,
//because you cannot use an index beyond the permitted range
//of fixed Vectors. 
//In this case the length is 20, and the only assignment can be to indices 0 to 19
```

With true (the default setting), the above 2 examples will behave the same in javascript at runtime as they would in AVM and in both cases generate a runtime error. However supporting this runtime behavior does generate extra code to achieve that result. In most cases it could be avoided to assist with performance. This is particularly relevant when index level assignments are made inside a loop. Often the loop variable is used as the index for the value assignment, and in this case, it is usually already certain to be within the valid range for the targetted Vector instance.  

For example:

```as3
var l:uint = myVec.length;  
for (var i:uint = 0; i<l; i++) {  
 myVec[i] = i/SOME_CONST; 
 //in the above case i is always in the valid range for myVec 
} 
```

In the above example, the compiler will by default be generating something in javascript that is (pseudocode) sort of like:
`myVec[myVec.checkIndex(i)] = i/SOME_CONST;` 

Where `myVec.checkIndex(i)` in the pseudocode checks that `i` is in the valid range for myVec, and returns it unchanged if it is, otherwise throws an error that corresponds to what would happen at runtime in AVM.

This is obviously not needed in the above case, and will definitely slow the loop down, so for performance reasons it is important to remove this generated code for large loops.  

So once everything has been verified to work correctly in your app, it is often a good idea to switch off the generation of this type of code.  
As with other settings it is possible to switch it off or on with more specificity by using [doc comment directives](create-an-application/optimizations/doc-comment-directives.html). 
If you are porting legacy as3 code, it can be useful to check that the code does not rely on error trapping for any of these cases before switching this setting off.

**Pro tip:** How do I know how much of my code is being affected by this setting? In javascript the **js&#x2011;debug** output, you can do a ***search in files*** for the string **Language.CHECK_INDEX**

## Dynamic access unknown members  {#dynamic-access-unknown-members}

**-js-dynamic-access-unknown-members**

When using plain objects the release version will try to "minify" renaming field names. Adding that option will make your code larger. 
Using data class definition instead of plain objects in all cases will defeat the need to use this option. Adding data classes will also make your code bigger, but it can also make it smaller depending on how many accesses there are to the object's properties. But data classes will also get compiler checking that you didn't mis-type a property name and various data-binding warnings will go away, which should improve your productivity.

