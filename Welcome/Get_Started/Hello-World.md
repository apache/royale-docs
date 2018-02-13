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
---

# Hello World

To verify that the Royale SDK is set up correctly, it is recommended to create and build a "Hello World" example.  If that works, you can move on to the ["Create an Application"](Create%20An%20Application.html) section and work through the tutorial on building a more substantial application.

## Create the project folders

Create or select a folder to hold this application's source and output.  

In that folder, create a folder called "HelloWorld" (it can be named something else if you want and can contain spaces).  This folder will be referred to as the "project" folder throughout the documentation.  

In the project folder, create a folder called src.  You can use other names, but the compiler will manage your output folders for you if you use "src" or "src/main/royale" ("src\main\royale" on Windows).

So, if you used a folder called "Projects" for all of your project folders, then you would have the following folders:

```
Projects
Projects/HelloWorld
Projects/HelloWorld/src
```

## Create the source file

In the src folder, create a file called HelloWorld.mxml and use your favorite text editor to give that file the following contents:

```xml
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

If you used NPM to install Royale, run from your project folder:

```
    mxmlcnpm src/HelloWorld.mxml
```

If you didn't use NPM, run:

```
    <path to SDK folder>/js/binmxmlc src/HelloWorld.mxml
```

## Run the output

If the compiler reported success, there should be a bin/js-release output folder in your project folder, such as 

```
    Projects/HelloWorld/bin/js-release
```

In there should be an index.html file you can open in your browser and you should see "Hello World" in your browser.  If you see that, congratulations!  You have installed Royale successfully and are ready to build Royale applications.  The ["Create an Application"](Create%20An%20Application.html) contains a tutorial for building a more substantial application.


