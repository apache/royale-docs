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
description: Refactoring code to remove circular dependencies
permalink: /compiler
---

# Apache Royale Compiler

Turn your source code into one or more compiled outputs

Royale provide a compiler and a command-line debugger to turn your source code into the required output. The compiler takes [AS3](features/as3) & [MXML](features/mxml) (and CSS) as inputs. 

The main output of the compiler is **JavaScript** (some call it a transpiler or cross-compiler). The compiler can also output **SWFs** for the **Adobe Flash** runtimes. There is some initial work on **Web Assembly** output.

> The compiler has been designed to make it relatively straightforward to add additional output formats.

The code is based on the ActionScript Compiler 2.0 donated to Apache by Adobe. The SWF output was pretty much working at the time of donation. The JavaScript output code is a new implementation by Apache committers

## User Guide

The Royale Compiler does many things besides compile **MXML** and **ActionScript** into **JavaScript** and/or **SWF**. But if that's all you want to do, you can use the compiler with **Apache Maven**, **Apache Ant**, several **IDEs**, **NPM** and the command-line. Below are some pointers to getting started:

### Apache Maven

There are some examples in the `apache/royale-asjs` repo in the `examples` folder. The `pom.xml` files should be useful as a starting point. There are also **Maven archetypes** available in Apache Royale releases.

### Apache Ant

In an Apache Royale distribution, there is a `compiler-royaleTasks.jar` in the `js/lib` folder that contains Ant tasks for the Royale Compiler. There is an mxmlc task for creating applications and a compc task for creating libraries.

### IDEs

Consult your IDE documentation for how to launch the Royale Compiler. You can generate a IDE distribution from Apache Maven and/or Apache ANT.

### NPM

You should be able to run `mxmlc` or `compc` from the command-line after installing Royale via NPM. Use `mxmlc --help` to see the latest list of options.

### Command-line

The `js/bin` folder should contain `mxmlc` and `compc` scripts that will launch the compiler. Use `mxmlc --help` to see the latest list of options.

## Compiler Options

Royale provide several compiler options to customize the use. You can check the list of compiler options here:

- [Compiler Options](compiler/compiler-options)

> To read about how to contribute to Apache Royale Compiler use the following [Apache Royale Compiler Developer Guide](https://github.com/apache/royale-compiler/wiki/Developer-Guide) available on the Apache Royale Compiler Wiki.