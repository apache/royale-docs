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
title: Command line compiler Usage
description: How to use the Apache Royale compiler
permalink: /compiler/command-line-compiler-usage
---

# Command line compiler usage

How to build from the command line

The [Apache Royale](https://royale.apache.org/) SDK contains a number of command line compilers that may be used to build your projects written in [MXML](features/mxml) and [ActionScript 3.0 (AS3)](features/AS3). Various [IDEs](get-started/development-tools) also offer commands to compile your Royale applications and libraries, which typically involves invoking these same command line compilers behind the scenes.

## Compilers

Several compilers are located inside the SDK's _js/bin_ directory. Each of these compilers serves a different purpose.

### `mxmlc`

The `mxmlc` compiler builds an Apache Royale application. It takes [MXML](features/mxml), [AS3](features/AS3), and CSS code as inputs, and it generates either JavaScript or SWF output.

### `compc`

The `compc` compiler builds a [_.swc_ library](libraries/library-basics). A _.swc_ file is a binary format that contains compiled code, but a library may also bundle asset files and API documentation that may be displayed by [IDEs](get-started/development-tools).

Distributing libraries as _.swc_ files instead of sharing the original source code files offers multiple advantages.

- Passing _.swc_ libraries to the `mxmlc` compiler makes application compilation faster because the compiler can simply copy the JavaScript or SWF bytecode that was already compiled by `compc`.

- Everything gets bundled into a single _.swc_ file, making it easier to configure your project and reducing the risk of losing or forgetting important dependencies.

### `asjsc`

The `asjsc` compiler is intended to cross-compile ActionScript 3.0 to JavaScript without using the Apache Royale framework components. It may be used for projects that want direct access to JavaScript APIs, like the [HTML Document Object Model (DOM) API](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model) or the [HTML Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API).

### `asnodec`

The `asnodec` compiler may be used to compile ActionScript 3.0 code to JavaScript that targets the [Node.js](https://nodejs.org/) cross-platform run-time. It provides an ideal way to use AS3 to create web servers, backends, and command line tools.

## Specifying configuration options

The command line compilers that are bundled with Apache Royale support a number of [configuration options](compiler/compiler-options) to customize their behavior. For example, the `-help` option may be passed to the compiler to display some basic documentation in your terminal.

```sh
mxmlc -help
```

The `-help` option supports several keywords for showing more detailed information.

To see instructions describing the correct syntax for running the compilers and specifying options, add the `syntax` keyword after the `-help` option. The information will be similar to what appears in this document.

```sh
mxmlc -help syntax
```

To see a list of common configuration options, add the `list` keyword after the `-help` option.

```sh
mxmlc -help list
```

To see a full list of all available configuration options, add the `advanced` keyword after the `-help` option.

```sh
mxmlc -help advanced
```

Append `aliases` after `-help list` or `-help advanced` to see any shorthand aliases available for each compiler option, if available.

Append `details` after `-help list` or `-help advanced` to see descriptions for each compiler option, if available.

Additional words passed to the `-help` option are treated as search terms. The following command searches for all compiler options that contain the word _include_ in their names or descriptions.

```sh
mxmlc -help advanced include
```

### Options with values

Most of the compiler's configuration options may be assigned one or more values.

Some configuration options accept a boolean value, which may be `true` or `false`. For instance, to disable compile-time warnings, you can add the `-warnings=false` option. If you specify a boolean option name without a value, that is shorthand for setting the value `true`. So `-warnings` without a value will enable compile-time warnings.

Other configuration options may accept numeric values or strings, including file paths. When compiling a library with `compc`, to specify the output path where the SWC file should be generated, you can add the `-output` option. For example, `-output=bin/my_library.swc` creates the SWC file in the _bin_ directory. All file paths may be either absolute or relative to the current working directory.

Some configuration options may require multiple values. The number of required values depends on the particular option. Separate the values with a comma (`,`) character. The list of values is terminated by omitting a comma after the final value. For example, the `-define` compiler option requires two values to name and initialize a compile-time constant. The `-define=CONFIG::CUSTOM_VALUE,123` option sets the `CONFIG::CUSTOM_VALUE` compile-time constant to a numeric value of `123`.

Some options are considered repeatable, which means that they may be set an unlimited number of times. For instance, the `-source-path` compiler option may be used to add multiple directories where the compiler can search for _.mxml_ and _.as_ source files.

Use the `+=` operator to append to a repeatable option. The `-source-path=src/main/royale` option replaces any current values in the list with a single value. The `-source-path+=src/main/royale` option preserves the existing list of values and appends a new path to the end.

An option may be cleared by setting `-option-name=` with no value following the equals sign.

The special string `--` may be used to terminate processing of named configuration options and to force any remaining values on the command line to be interpreted as default arguments.

Configuration options sometimes have shortened aliases that make them easier to type. For instance, the `-output` option has an alias `-o`. Hierarchical dotted variable names will automatically have an alias generated for their "leaf" name, if it is unique. For example, `-compiler.keep-as3-metadata` has an alias `-keep-as3-metadata`.

## Using `mxmlc`

Typically, one _.mxml_ or _.as_ file is passed to the `mxmlc` compiler, and it is treated as the Royale application's entry point.

```sh
mxmlc src/Main.mxml
```

By default, the compiler will automatically detect the directory that contains the _.mxml_ or _.as_ file as a source path where other definitions (classes, interfaces, etc.) may be found. However, if the entry point is in a package, you can specify a source path manually.

In the following example, the entry point is a class named `Main`, which is in the `com.example` package. To prevent the compiler from treating _example_ as the root of the source path instead pf _src_, specify the `-source-path` compiler option before specifying the path to the entry point class.

```sh
mxmlc --source-path+=src src/com/example/Main.mxml
```

If you have MXML or AS3 source files in multiple directories, you may append each of them to the source path.


```sh
mxmlc --source-path+=src --source-path+=path/to/another/src src/Main.mxml
```

If you need to use a SWC library in your application, you may add the _.swc_ file to the library path.

```sh
mxmlc --library-path+=libs/ThirdPartyLibrary.swc src/Main.mxml
```

> If the definitions from the SWC file are not recognized by the compiler, it may be because the `-js-library-path` or `-swf-library-path` options are specified. These take precedence over `-library-path`. In that case, you can append to one of those options instead of `-library-path`.
>
> ```sh
> mxmlc -js-library-path+=libs/ThirdPartyLibrary.swc src/Main.mxml
> ```

If you need to use _multiple_ SWC libraries in your application, and they are all contained within the same directory, you may add the directory to the library path.

```sh
mxmlc --library-path+=libs src/Main.mxml
```

## Using `compc`

To specify the file path where the SWC library will be created, use the `-output` compiler option.

```sh
compc -output=bin/ExampleLibrary.swc
```

However, specifying the output path is not enough to build a library. A library should include one or more definitions (classes, interfaces, etc.), which may be configured with one or more additional compiler options.

- `-include-classes` specifies a list of specific classes (and their dependencies) to include in the SWC library.
- `-include-namespaces` specifies that all definitions defined in a particular MXML namespace should be included in the SWC library.
- `-include-sources` specifies that all definitions found in the specified directory (including sub-directories) should be included in the SWC library.

To use the `-include-classes` option, start by specifying at least one directory to use as a source path root where the compiler can search for _.mxml_ and _.as_ files. Then, specify the fully-qualified names of each class to include. A fully-qualified class name includes its base name and the name of the package that contains it. The fully qualified name of a class named `MyClass` in the `com.example` package is `com.example.MyClass`.

```sh
compc -source-path+=src -include-classes+=com.example.controls.ExampleControl -include-classes+=com.example.utils.ExampleUtil -output=bin/ExampleLibrary.swc
```

To use the `-include-namespaces` option, start by specifying at least one directory to use as a source path root, where the compiler can search for _.mxml_ and _.as_ files. Then, define an MXML namespace by specifying a unique URI that you create (typically using a domain name that you own, but the URI isn't necessarily intended to actually exist on the web) and the path to a [component manifest XML file](libraries/compiled-code-libraries#the-manifest) that maps the fully-qualified class names of all components in the namespace to identifiers used in MXML.

The following is an example component manifest XML file. It is named _manifest.xml_, for simplicity (but any file name is allowed).

```xml
<?xml version="1.0"?>
<componentPackage>
    <component id="ExampleControl" class="com.example.controls.ExampleControl"/>
    <component id="AnotherExampleControl" class="com.example.controls.AnotherExampleControl"/>
</componentPackage>
```

The custom namespace URI used in the following example will be `https://ns.example.com/mylib`.

```sh
compc -source-path+=src -namespace+=https://ns.example.com/mylib,manifest.xml -include-namespaces+=https://ns.example.com/mylib -output=bin/ExampleLibrary.swc
```

To use the `-include-sources` option, start by specifying at least one directory to use as a source path root, where the compiler can search for _.mxml_ and _.as_ files. Then, use the same path to include all definitions in it.

```sh
compc -source-path+=src -include-sources+=src -output=bin/ExampleLibrary.swc
```

To reference other libraries when compiling your SWC library, use either the `-external-library-path` option or the `-library-path` option.

```sh
compc -external-library-path+=libs/ThirdPartyLibrary.swc -source-path+=src -include-sources+=src -output=bin/ExampleLibrary.swc
```

> **What's the difference between `-external-library-path` and `-library-path` in `compc`?**
>
> There are tradeoffs, with each option having certain advantages and disadvantages.
>
> Using `-external-library-path` with `compc`, you can reference definitions from _ThirdPartyLibrary.swc_ without including those definitions into _ExampleLibrary.swc_. If a new version of _ThirdPartyLibrary.swc_ is released, and there are no breaking changes to the APIs in _ThirdPartyLibrary.swc_, only the application needs to be recompiled with `mxmlc`. The _ExampleLibrary.swc_ may not need to be recompiled with `compc`. However, when you use `-external-library-path`, you must pass both _ExampleLibrary.swc_ and _ThirdPartyLibrary.swc_ to `mxmlc` when compiling the application.
>
> Using `library-path` with `compc`, the definitions from _ThirdPartyLibrary.swc_ will be copied into _ExampleLibrary.swc_. If a new version of  _ThirdPartyLibrary.swc_ is released, _ExampleLibrary.swc_ will need to be recompiled with `compc`, and then, the application will need to be recompiled with `mxmlc`. However, only _ExampleLibrary.swc_ needs to be passed to `mxmlc` because it will already include the definitions from _ThirdPartyLibrary.swc_.
