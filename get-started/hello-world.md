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
title: Hello World
description: Try the simplest piece of code possible
permalink: /get-started/hello-world
---

# Hello World

Try the simplest piece of code possible

To verify that the Royale SDK is set up correctly, we recommend you create and build a ["Hello World"](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program){:target='_blank'} example. If that works, you can move on to [Create an Application](create-an-application) and work through the tutorial on building a more substantial application.

These instructions presume you are not using an [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment){:target='_blank'}, but are creating files in a text editor and compiling using command-line scripts or similar controls. [Development tools](get-started/development-tools) that fully support Royale provide their own instructions for building your first Royale applications.

> In our Apache Royale Blog Examples, you can read about the ['Hello World' example](https://royale.apache.org/creating-a-hello-world-in-apache-royale/) to complement the information exposed here. Notice that the main difference is that while in this Hello World we use the _Express_ library, in the blog example we use the _Basic_ version that requires a few more lines of code.

## Create the project folders

Create or select a folder to hold this application's source and output.  

In that top-level folder, create a folder called `HelloWorld` (it can be named something else if you want, and the name can contain spaces). This folder will be referred to as the `project` folder throughout the documentation.  

In the project folder, create a folder called `src`. You can use other names, but the compiler will manage your output folders for you if you use `src` or `src/main/royale` (`src\main\royale` on Windows).

So, if you used a folder called `Projects` for all of your project folders, then you would have the following folders:

```
Projects
Projects/HelloWorld
Projects/HelloWorld/src
```

## Create the source file

In the `src` folder, create a file called `HelloWorld.mxml` and use your favorite text editor to give that file the following contents:

```mxml
<?xml version="1.0" encoding="utf-8"?>
<js:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
                xmlns:js="library://ns.apache.org/royale/express">

    <js:initialView>
        <js:View>
            <js:Label text="Hello World" />
        </js:View>
    </js:initialView>
</js:Application>
```

## Compile the source file

If you used [NPM](https://www.npmjs.com/){:target='_blank'} to install Royale, run from your project folder:

```sh
mxmlcnpm src/HelloWorld.mxml
```

If you didn't use npm, run:

```sh
<path to SDK folder>/js/bin/mxmlc src/HelloWorld.mxml
```

## Run the output

If the compiler reported success, there should now be a `bin/js-release` output folder in your project folder, such as 

```
Projects/HelloWorld/bin/js-release
```

In that folder should be an `index.html` file you can open in your browser to see your "Hello World" application.  If you see that, congratulations! You have installed Royale successfully and are ready to build Royale applications.  

[Create an Application](create-an-application) contains a tutorial for building a more substantial application. The Royale SDK includes an **Examples** directory that provides practical demonstrations of how to achieve many features and effects using Royale.
