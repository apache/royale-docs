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
title: Compiler
description: Using the Royale compiler to create release artifacts
permalink: /compiler
---

# Apache Royale Compiler

Turn your source code into compiled output

[Apache Royale](https://royale.apache.org/) provides a compiler (some call it a transpiler or cross-compiler) and a command-line debugger to turn your source code into compiled output you can share with users. The compiler takes [AS3](features/as3), [MXML](features/mxml), and CSS as inputs. 

The main output of the compiler is **JavaScript**. The compiler can also output the **SWF** format for the **Adobe AIR** and **Adobe Flash Player** runtimes. There is some initial work on **Web Assembly** output.

> The compiler is architected in a way to make it possible to add additional output formats in the future.

The code is based on the <a href="https://web.archive.org/web/20171025115551/https://www.adobe.com/content/dam/acom/en/devnet/air/pdfs/adobe-actionscript-compiler-20-release-notes.pdf" target="_blank">ActionScript Compiler 2.0</a> that Adobe donated to Apache. The SWF output was pretty much working at the time of donation. Volunteers working on the Apache Flex and Royale projects have created the JavaScript output code.

## User Guide

The Royale Compiler does many things besides compile **MXML** and **ActionScript** into **JavaScript** and/or **SWF**. But if that's all you want to do, you can use the compiler with <a href="https://maven.apache.org/" target="_blank">Apache Maven</a>, <a href="https://ant.apache.org/" target="_blank">Apache Ant</a>, <a href="https://github.com/BowlerHatLLC/asconfigc" target="_blank">asconfigc</a>, several [IDEs](get-started/development-tools), <a href="https://www.npmjs.com/" target="_blank">npm</a> and through the command-line. Below are some pointers to getting started:

### Apache Maven

<a href="https://maven.apache.org/" target="_blank">Apache Maven</a> is a command line tool for automating builds, and a plugin is available for compiling for Royale projects. There are some examples in the **apache/royale-asjs** repo in the _examples_ folder. The _pom.xml_ files should be useful as a starting point. There are also **Maven archetypes** available in Apache Royale releases.

### Apache Ant

<a href="https://ant.apache.org/" target="_blank">Apache Ant</a> is a command line tool for automating builds, and custom tasks are available for compiling Royale projects. In an Apache Royale distribution, there is a _compiler-royaleTasks.jar_ in the _js/lib_ folder that contains Ant tasks for the Royale compiler. There is an **`<mxmlc>`** task for compiling applications and a **`<compc>`** task for compiling SWC libraries.

Add the following to your Ant build script to load the custom Ant tasks for the Royale compiler:

```xml
<taskdef resource="flexTasks.tasks" classpath="${env.ROYALE_HOME}/js/lib/compiler-royaleTasks.jar"/>
```

If you don't have the `ROYALE_HOME` environment variable defined, replace `${env.ROYALE_HOME}` with the path to your SDK.

Then, you can use the **`<mxmlc>`** and **`<compc>`** tasks in your Ant build script.

### asconfigc

[**asconfigc**](https://www.npmjs.com/package/asconfigc) is a command line tool for compiling ActionScript and MXML projects configured with an <a href="https://github.com/BowlerHatLLC/vscode-as3mxml/wiki/asconfig.json" target="_blank">_asconfig.json_</a> file.

The <a href="https://github.com/BowlerHatLLC/vscode-as3mxml/wiki/asconfig.json" target="_blank">_asconfig.json_</a> file format was originally designed for the [ActionScript & MXML language extension for Visual Studio Code](https://github.com/BowlerHatLLC/vscode-as3mxml/wiki), as a way to enable code intelligence features and run build tasks. Later, **asconfigc** was released as a separate command line tool that could read <a href="https://github.com/BowlerHatLLC/vscode-as3mxml/wiki/asconfig.json" target="_blank">_asconfig.json_</a> configuration files and launch the compiler with appropriate options outside of Visual Studio Code.

Refer to the <a href="https://github.com/BowlerHatLLC/vscode-as3mxml/wiki/asconfig.json" target="_blank">_asconfig.json_ documentation</a> for the full list of project configuration options.

### IDEs

Consult the documentation for your [IDE or editor](getting-started/development-environment) to learn how how to launch the Royale compilers. If [building the SDK from source](https://github.com/apache/royale-asjs/wiki/Building-From-Source), you can generate a distribution compatible with IDEs using either Apache Maven or Apache Ant.

### NPM

Both the **mxmlc** application compiler and the **compc** library compiler will be available on the system path to run from the command line after [installing Royale via npm](get-started/download-royale#npm) with the `-g` flag. Use `mxmlc --help` or `compc --help` to see the [list of available compiler options](compiler/compiler-options).

### Command line

The _js/bin_ directory in the SDK contains the **mxmlc** and **compc** scripts that will launch the compilers. Use `mxmlc --help` or `compc --help` to see the [list of available compiler options](compiler/compiler-options).

To use **mxmlc** to compile a Royale application, pass the path to the target file that will be the application's entry point.

```sh
mxmlc src/MyApp.mxml
```

Additional [compiler options](compiler/compiler-options) may be specified as well. The following options specify that the app should be built for JavaScript only, it should be a debug build, and that source maps should be generated for debugging.

```sh
mxmlc -targets=JSRoyale -debug=true -source-map=true src/MyApp.mxml
```

## Compiler Options

Royale provides several compiler options to customize the use. You can check the list of compiler options here:

- [Compiler Options](compiler/compiler-options)

> Read about <a href="https://github.com/apache/royale-compiler/wiki/Developer-Guide" target="_blank">how to contribute to the Apache Royale Compiler</a>.