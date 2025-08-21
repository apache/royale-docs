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
title: Minification
description: Options and considerations for minimized JavaScript output
permalink: /create-an-application/optimizations/minification
---
# Minification

Minification is the process of minimizing code and markup in your application. It's one of the main methods to reduce load times and improve application performance.

Here are options and considerations for minimizing JavaScript output in your [Apache Royale](https://royale.apache.org/) application.

## Default behavior
By default, Royale outputs a single minified JavaScript file for deployment of the application. The minified file contains all the code needed for running your application. The code contains the necessary pieces of framework code as well as your application code. The minification uses Google's Closure Compiler. The goal for the default release output is that it should always work without consideration for how the code was written.

## What's in the release code
To ensure that all features work correctly, the output by default keeps all public class and member names. The process renames and minifies the inner workings when possible, but keeps the original name in the code. This results in code which works and is reasonably compact. 

There are two reasons you might want to consider using additional compiler options.
1. You can get your release code to be 20-30% smaller by enabling more aggressive minification.
2. Using the default export options, it's fairly straightforward to browse your release JavaScipt code to get an idea of how the application was constructed. Aggressive minification will make your application much more opaque and reverse-engineering it will become much more difficult.

## Relevant compiler options
There are numerous [compiler options](compiler/compiler-options) which you can use for minification, and turn on or off for specific cases. For full details, [read the whole page](compiler/compiler-options). Most cases of advanced minification use the following options:

### Smallest size option {#smallest-size}
```
-export-public-symbols=false
-prevent-rename-protected-symbols=false
-prevent-rename-public-symbols=false
-prevent-rename-internal-symbols=false
```

This combination of options will produce the most compact code.

Some additional options which will reduce code size (and improve performance) are:

```
-js-output-optimization=skipAsCoercions
-js-vector-emulation-class=Array
-js-vector-index-checks=false
-js-complex-implicit-coercions=false
```

An additional one which will have a small effect on code size, but will not effect performance and might introduce bugs if turned off is:
```
-js-default-initializers=false
```
Make sure you read the [compiler options](compiler/compiler-options) page to understand what each of these options does.

There is one option which will make some of the output code larger, but might be necessary in many situations:
```
-js-dynamic-access-unknown-members=true
```

We discuss this option in length below.

## Considerations
Before using advanced minification options, you need to consider your application needs:
1. Do you have plain objects (i.e. JSON) where the names of properties are important? If yes, those can not be renamed.
2. Are you using external JS libraries without proper type definitions?
3. Do you use dynamic bracket access for members? If yes, are the keys hard-coded or inferred?
4. Do you access static class members without knowing the specific class? (i.e. `classVar.fooBaz()`)

## Solutions
If you answer no to all of the above questions, you can use the [smallest size options](create-an-application/optimizations/minification#smallest-size).

If you answered yes to #1 and #2 above, you need to ensure that your dynamic object access is not renamed. Otherwise you will end up with `myJSON.a` instead of `myJSON.thumbnail` and you will get unexpected `undefined` values. There are two ways to do this.
1. Manually quote every case of dynamic access (i.e. `myJSON["thumbnail"]` instead of `myJSON.thumbnail` and `{"name":"foo","age":20}` instead of `{name:"foo",age:20}`)
2. Have the compiler do this for you automatically.

The compiler option to do this automatically is `-js-dynamic-access-unknown-members=true`. However, bear in mind that the compiler will quote **every** instance of dynamic access. Using `-js-dynamic-access-unknown-members=true` together with the other minification options can break using your app if you don't declare your types correctly **everywhere** in your app, including arrays. If you try `myArray[i].doSomething()` with the combination of compiler options above, your app **will** break. That's because the type of `myArray[i]` is unknown. The compiler does not know if it's a `Foo` or an `Object` with dynamic access which cannot be renamed.

## Choose your path
If you need to keep dynamic names, decide if it's better or less work to manually quote the cases where you need to keep the names of dynamic access, or if you want to ensure you're meticulous about declaring types in your application.

Going the path of declaring types has the advantage of giving your app more type safety and preventing bugs, but can be more work.

## Suggestions
### Use `Vectors` instead of `Arrays`
Vectors give the compiler the information it need about types so it knows not to quote access. It also gives you better type safety, so it's a good idea in general. Read the [Vector](features/as3/vectors) page for more details.

### Audit use of `:Object` and `:*`
If you are using a dynamic type, make sure that there's a compelling reason to do so.

### Use interfaces
[Interfaces](features/as3/interfaces) are a powerful tool for declaring your types. You can use interfaces for even unrelated types which have similar access. Interfaces can be a good choice in many cases where you might be tempted to use Object.

### Search your debug js files
You can get lots of clues to places where you should have done a better jobs of declaring types by searching your JS files for `["` or `"]`. That will find bracketed access. The pattern of `"](` is especially suspect because that indicates calling a method on a dynamic object.

### Be wary of `for in`
`for in` is a prime candidate for introducing problematic dynamic access. You can use `for in` for dynamic objects or statically-typed objects, but mixing the two will not work. `myClassInstance[x] = myObject[x]` will **not** work.

### Pause on exceptions
Sometimes you are going to have to run your minified code and find what broke. Pausing on caught exceptions is often a good way to find **where** your code breaks. Search the surrounding code for un-minified variables or patterns that you might recognize from your source code. Going back to your source code, you can usually figure out what value was not assigned correctly. That should give you clues to where access is broken.

### Run your app in release mode often
Constantly checking that your app works both in debug and release mode is important for finding where you might break your app.

## Features which affect file size
In general, only dependencies you need are included in your app when using Royale. Usually this means additional classes and the associated code. In certain cases, using features will affect the size of *all* your classes because more information will be needed at runtime.
1. Reflection classes and functions. (To do -- needs a page) (i.e. `getDefinitionByName`, `getQualifiedClassName`, etc.) If you use reflection, information about your classes and accessors is needed at runtime. This adds significantly to the size of your runtime output. If you just need to get the class from an instance, you **do not** need reflection (unlike in Flash). There is `org.apache.royale.utils.object.classFromInstance()`, which helps with this without a reflection dependency.
2. [AMF](working-with-data/loading-external-data/amf). AMF uses reflection under the hood to recreate classes from data at runtime. If AMF is important to you, the extra weight might be justified, but make an informed decision.
3. [Crux](libraries/crux). Crux uses reflection as well. If dependency injection is your thing, then Crux is a solution; but you should be aware of the cost it brings.
