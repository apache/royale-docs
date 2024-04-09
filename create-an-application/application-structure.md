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
title: Application structure
description: All about the organization of your project files and folders
permalink: /create-an-application/application-structure
---

# Application structure

All about the organization of your project files and folders

[Apache Royale](https://royale.apache.org/) applications usually include many files. If you are in rapid-prototyping or proof-of-concept "get something small running quickly" mode, you can cram everything into one file. But breaking things into multiple pieces often helps you organize your code and create "separation of concerns"; and as your project and team grows, you and your teammates can work on individual pieces independently without stepping on each other's work. Finally, you can more easily re-use coherent pieces that perform some standard function or provide a common user experience (like a login form and its related logic) in other applications.

There are multiple popular ways of dividing an application into coherent and reusable pieces: Model-View (MV), Model-View-Controller (MVC), and other alphabet soup like MVP, MVVM, HMVC and more. This documentation will not address these patterns in detail. You can read more about them on the internet.

> Whatever you decide for how many files you will have, another thing to keep in mind is that Royale can produce different kinds of output, like SWFs for Adobe FlashPlayer or Adobe AIR and HTML/JS/CSS files for browsers and Apache Cordova applications. So, the recommended practice is to create a folder for your project files and a set of subfolders within it. The Royale compiler detects certain common folder patterns and automatically chooses where to put output folders, although you can override that if you desire.

If you are using an [IDE](get-started/development-tools) that supports Royale, it will create the standard folder structure for you when you create a Royale project. If you are working outside of an IDE, and perhaps using command-line instructions to compile your code, here is how to structure your project.

Let's say you are creating a project called `MyFirstRoyaleApp`. Create a `MyFirstRoyaleApp` folder and in it create a folder named `src`. Put your source code in there. If you do that, the compiler will put the output in a `bin` folder that it creates.

If you use [Apache Maven](https://maven.apache.org){:target='_blank'} to build your app, you can use one of the [Maven archetypes](get-started/development-tools.html#apache-maven), which put the main application source code 3 levels deep in a `src/main/royale` folder structure. Other kinds of files then go in `src/main/resource`, `src/main/config` and so on. Maven instructs the compiler to put the output in a `target/javascript/bin` folder.

Most Royale applications use an [MXML](features/mxml) file as the main application file. Write other files in MXML or [ActionScript](features/as3) depending on whether you are assembling pieces or writing custom logic. You can write a Royale application without using MXML at all, but you'll end up writing more code.

So, if you decide to use MXML as your main application file, your folder structure might look like this:

```
-MyFirstRoyaleApp
|-src/MyFirstRoyaleApp.mxml
```

And after compilation you will see:

```
-MyFirstRoyaleApp
|-src
   |-MyFirstRoyaleApp.mxml
|-bin
   |-js-debug
      |-index.html
      |-MyFirstRoyaleApp.js
      |-MyFirstRoyaleApp.css
      |-(lots of other files)
```

If you create a production version, you will also see:

```
|-bin
   |-js-release
      |-index.html
      |-MyFirstRoyaleApp.js
      |-MyFirstRoyaleApp.css
```
