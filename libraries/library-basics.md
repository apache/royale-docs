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
title: Library Basics
description: What are libraries in Royale
permalink: /libraries/library-basics
---

# Royale libraries

A bit about [Apache Royale](https://royale.apache.org/) libraries. What they are, how to use them and how to create them.

Royale libraries are packaged in `swc` files. A `swc` file is a zipped archive which contains the following:
1. A `catalog.xml` which describes what is in the archive.
2. A `library.swf` file which is binary representation of the code structure in Flash format. The compiler reads this file to determine type information and code flow.
3. Optionally, a `js` folder which contains compiled JavaScript code which a JavaScript runtime can run.

## Types of libraries
There are two basic library types:
1. Compiled Code libraries
2. Typedef libraries

There is no obvious way to tell the difference. Both have a `.swc` extension, although typedef libraries do not have any `js` code included and will generally be smaller.

### Compiled Code libraries
Compiled code libraries contain code that will end up in your compiled application (assuming you use that code). A library can contain code that you might use internally across multiple projects, or it can be a library that someone else compiled, and that provides functions that some part of your application needs. Much of the Royale framework is compiled into `swc` files that applications use.

Compiled code libraries are created using the `compc` compiler. See [detailed instructions on how to create one](libraries/compiled-code-libraries).

### Typedef libraries
Typedef libraries define the types of different classes, but contain no code that would be added to an application. Typedef libraries hold core Web APIs and third party JavaScript libraries which could be included in applications as separate JavaScript files (such as jQuery). Typedef libraries are similar to Typescript `d.ts` files.

Typedef libraries are created using the `externc` compiler. (TODO add sample configs for doing this.)

For completeness' sake: There's a third class of libraries which you would generally not need to deal with. That's the `GCL library` included in Royale. It has the type definitions for Google Closure Library, but the actual code that your application might use comes from the Google Closure Library JavaScript files. (TODO -- edit this for accuracy)

## Using SWC libraries

To use a `swc` library, include the `swc` file in your project. Royale framework `swc`s are available automatically, but you can include any `swc` you want by adding the file. To use compiled code libraries, specify the containing folder using `library-path` and/or `js-library-path`. (TODO add links to compiler arguments)

## Creating SWC libraries

TODO fill this out
