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
title: Modules
description: Break your application in parts
permalink: /features/modules
---

# Modules

Break your application in parts

Royale supports a distributed development model called **modules**. Those familiar with [Apache Flex](https://flex.apache.org/){:target='_blank'} SDK will recognize the term. Royale modules work almost identically to Flex modules with a few differences.

An example of an Application loading a Module can be seen below:

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="300" 
src="assets/BE0013_Dividing_an_Apache_Royale_application_with_modules/index.html"></iframe>

## Why modules?

As your application grows in size, you have to load more and more code just to show the first screen. A complex application will have many screens, and the first screen may just be something simple like the login page. Your users may be on slow, busy, or expensive networks, so you want to load as little code as possible to show the first screen, and load other code in the background or on-demand.

Also, as your application grows in size, the number of files of code you will grow and compile-time will increase. You may have teammates helping develop some of these files. Having to coordinate changes in the various files and wait for long compile-times is expensive. If you have properly designed your application, you know that not every file needs to be re-compiled when other files change, so having one teammate work on one set of files while you work on another saves time and hassle.

A `Module` is a separate compilation of one or more source files that results in output that can be loaded when it is needed by the main application.

A `Module` can contain code that doesn't have a UI, or it can be mostly UI. Modules can provide other UI screens and associated logic. There is a `ModuleLoader` component that displays the components that are children of a module. MXML files are commonly used to specify the UI components.

There is an example for [Basic](component-sets/basic) UI Set [here](https://github.com/apache/royale-asjs/tree/develop/examples/royale/ModuleExample){:target='_blank'} and other for [Jewel](component-sets/jewel) UI Set can be found [here](https://github.com/apache/royale-asjs/tree/develop/examples/blog/BE0013_Dividing_an_Apache_Royale_application_with_modules){:target='_blank'}.

Proper use of modules can help maintain _"separation of concerns"_ which helps keep you from writing _"spaghetti code"_. If only the code in one module changes, only that module needs to be recompiled. And if that code isn't needed to show the first screen, then the application might start up faster if that module is loaded only when it is needed.

## Why not modules? {#why-not-modules}
In Flash, modules was very important. That's because application size and compilation time grew very rapidly. Flash applications were slow to load and modules were a good tool to help with that. The aggressive use of PAYG in Royale along with browser features for loading Javascript made Royale applications much smaller and load times generally nearly instant. In many (most?) use cases of modules for Flex applications in Flash, Royale renders them unnecessary.

Using modules can make development more difficult and in some cases cause your application to actually load _**slower**_. Before using modules, consider the following points:

* You will see huge drops in compilation speed when switching from Flash to HTML Royale for the same application.
* The application size dropped drastically as well, and the whole application will often become about the size of a single module.
* Network speeds have improved drastically over the last 10 years so many of the considerations have changed.
* JS caching in the browser is much better than Flash caching was. You can setup your deployments so your application resource files (js, css, etc.) are cached for 30 days and when deploying a new version, the cache is automatically invalidated.
* Using modules limits how aggressively code can be minified. Improved minification helps both in deployed code size and speed of code execution.
* A large part of application and module size in Flash was caused by embedded assets. In HTML, assets are stored externally and only loaded when/if they are actually needed.

## Compiling modules

Typically, you develop a module in a separate folder of source files, and generate the output as a sibling to the other source files, which then cannot be easily accessed by the output of the main app. In JavaScript output, in development mode, the compiler generates lots of files. All these files must be relocated into the main app's output folder so the main app can reference them via the same relative path when the module is compiled into a single output file in production mode.

The Royale compiler supports a `-module-output=<destination folder>` that redirects where the output goes in order to place the development output in the right place. This is useful in some cases when using module that are in the same source path as the main app as opposed to being in separate projects.

> For example in TourDeFlex, the main app is in the `src` folder, and a module example may be in `src/mx/controls/` such as `mx/controls/ButtonExample.mxml`. Without this options, the output might end up in `src/mx/controls/bin/js-debug` and `src/mx/controls/bin/js-release` when it would be better if the output was relative to the main app and go in `bin/js-debug/mx/controls` and `bin/js-release/mx/controls`. Even specifying js-output doesn't work as setting it to the main app's bin folder would result in the output .JS going in the same folder as the main app instead of being nested in mx/controls.  So, by setting this option to mx/controls, the compiler will calculate the desired folder structure.

For complex scenarios (i.e: each module is a separate project), the user can automate copying files to other locations as we do in this [example](https://github.com/apache/royale-asjs/tree/develop/examples/blog/BE0013_Dividing_an_Apache_Royale_application_with_modules){:target='_blank'}.

## Minification and modules {#minification}
When code is deployed, the code is minified and parts are renamed in an unpredictable way. This means that you can't know ahead of time what things will actually be called in your application.

For normal applications this is generally not an issue unless you want to enable [advanced minification options](create-an-application/optimizations/minification).

For modules, this is a very big issue because the modules are compiled in a separate session than the main application and each other. To make modules work correctly you need to use special compiler options while compiling both your main application and your modules. There are four compiler options that are relevant to this which are all specified in the `js-compiler-option` section of the compiler arguments:

```
--variable_map_input_file [path to unique file name]
--property_map_input_file [path to unique file name]
--variable_map_output_file [path to unique file name]
--property_map_output_file [path to unique file name]
```

The `*output_file` options must be used when compiling your main application. The `*input_file` options must be used when compiling your modules. If you have multiple modules that might depend on each other, you will need the `*output_file` options for the modules as well.

[CLARIFY -- Is a separate file needed for each module, or can a single output file be used for the whole application?]

Here is what the config file for the main app example modules project:

```
<royale-config>
    <js-compiler-option>
        <option>--variable_map_output_file gccvars.txt</option>
        <option>--property_map_output_file gccprops.txt</option>
    </js-compiler-option>
</royale-config>
```

Here's the config for the module:

```
<royale-config>
    <js-compiler-option>
        <option>--variable_map_input_file ../../../MainApp/bin/js-release/gccvars.txt</option>
        <option>--property_map_input_file ../../../MainApp/bin/js-release/gccprops.txt</option>
        <option>--variable_map_output_file modgccvars.txt</option>
        <option>--property_map_output_file modgccprops.txt</option>
    </js-compiler-option>
</royale-config>
```
## Using modules

`Modules` are loaded by specifying the path to the main JavaScript file for the module. If you are also working with Flash/AIR output, you can specify the .swf suffix and the Royale `ModuleLoader` will replace that with .js as needed.

## Differences from Flex modules

An important difference between Flex modules and Royale modules is how memory is managed. Flash/AIR runtimes support the concept of unloadable code via the `ApplicationDomain` class. If you load a SWF in Flash or AIR and then remove all references to its code and instances, the SWF and related code definitions will be freed from memory.

There is currently no emulation of `ApplicationDomain` in Royale. Royale modules all load into the same global variable scope as the main application. It might be possible to emulate `ApplicationDomain`, but it will likely be expensive.

The benefit of having unloadable code in JavaScript may not be as compelling as it is for Flash/AIR. In Flash, SWFs are compressed binaries that cannot be further compressed when downloaded over the network. The code in a SWF is intermediate byte code instead of plain text that has been minified. And Flash always just-in-time compiled intermediate byte code. Different browsers will have different behaviors when interpreting JavaScript.

Seeing the module unload in Flex/AIR apps was a good test that all of the instances associated with the module had been freed. But it was almost always true that the amount of memory allocated to these instances was much more than the overhead of the code itself. In Royale, the cost of leaving class definitions in global memory plus the memory for the actual module's JavaScript source may not be the reason your application runs out of memory. The real trick will be determining what instances are still stuck in memory and how to get rid of them.


