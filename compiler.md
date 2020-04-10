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

Royale provides a compiler (some call it a transpiler or cross-compiler) and a command-line debugger to turn your source code into compiled output you can share with users. The compiler takes [AS3](features/as3), [MXML](features/mxml), and CSS as inputs. 

The main output of the compiler is **JavaScript**. The compiler can also output **SWF**s for the **Adobe Flash** and **AIR** runtimes. There is some initial work on **Web Assembly** output.

> It is relatively straightforward to add additional output formats to the compiler.

The code is based on the <a href="https://www.adobe.com/content/dam/acom/en/devnet/air/pdfs/adobe-actionscript-compiler-20-release-notes.pdf" target="_blank">ActionScript Compiler 2.0</a> that Adobe donated to Apache. The SWF output was pretty much working at the time of donation. Volunteers working on the Apache Flex and Royale projects have created the JavaScript output code.

## User Guide

The Royale Compiler does many things besides compile **MXML** and **ActionScript** into **JavaScript** and/or **SWF**. But if that's all you want to do, you can use the compiler with <a href="https://maven.apache.org/" target="_blank">Apache Maven</a>, <a href="https://ant.apache.org/" target="_blank">Apache Ant</a>, several [IDEs](get-started/development-tools), <a href="https://www.npmjs.com/" target="_blank">npm</a> and through the command-line. Below are some pointers to getting started:

### Apache Maven

There are some examples in the `apache/royale-asjs` repo in the `examples` folder. The `pom.xml` files should be useful as a starting point. There are also **Maven archetypes** available in Apache Royale releases.

### Apache Ant

In an Apache Royale distribution, there is a `compiler-royaleTasks.jar` in the `js/lib` folder that contains Ant tasks for the Royale Compiler. There is an mxmlc task for creating applications and a compc task for creating libraries.

### IDEs

Consult your IDE documentation for how to launch the Royale Compiler. You can generate an IDE distribution from Apache Maven and/or Apache ANT.

### NPM

You should be able to run `mxmlc` or `compc` from the command line after installing Royale via npm. Use `mxmlc --help` to see the latest list of options.

### Command line

The `js/bin` folder should contain `mxmlc` and `compc` scripts that will launch the compiler. Use `mxmlc --help` to see the latest list of options.

## Compiler Options

Royale provides several compiler options to customize the use. You can check the list of compiler options here:

- [Compiler Options](compiler/compiler-options)

> Read about <a href="https://github.com/apache/royale-compiler/wiki/Developer-Guide" target="_blank">how to contribute to the Apache Royale Compiler</a>.
