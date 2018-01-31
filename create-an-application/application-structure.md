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
---

# Application structure

Royale applications are usually comprised of multiple files.  If you are in rapid-prototyping or proof-of-concept "get something small running quickly" mode, you can cram everything into one file.  But breaking things into multiple pieces often helps you organize or create "separation of concerns" and as your project and team grows, you and/or your teammates can work on individual pices independently without stepping on each other's work.  And those pieces often have a greater chance of being re-used in other applications.

There are multiple popular ways of dividing up an Application into pieces.  There is Model-View (MV), Model-View-Controller (MVC), and now other alphabet soup like MVP, MVVM, HMVC and more.  This documentation will not address these patterns in detail.  You can read more about them on the internet.

Whatever you decide for how many files you will have, another thing to keep in mind is that Royale can produce different kinds of output, like SWFs for Adobe FlashPlayer or Adobe AIR as well as HTML/JS/CSS for browsers as well as Apache Cordova applications.  So, the recommended practice is to create a folder for your project files and a set of subfolders within.  The Royale compiler detects certain common folder patterns and automatically chooses where to put output folders, although you can override that if you desire.

Let's say you are creating a project called MyFirstRoyaleApp.  Create a MyFirstRoyaleApp folder and in it create a folder named "src" and put your source code in there.  If you do that, the compiler will put the output in a "bin" folder".

If you are going to use Apache Maven to build your app, you can use one of the Maven archetypes, which put the main application source code 3 levels deep in a "src/main/royale" folder tree.  Other kinds of files then go in "src/main/resource", "src/main/config" and more.  Maven will instruct the compiler to put the output in a "target/javascript/bin" folder tree.

Most Royale applications use an MXML file as the main application file.  Other files are written in MXML or ActionScript depending on whether you are assembling pieces or writing custom logic.  You can write a Royale Application without using MXML at all, but you'll end up writing more code.

So, if you decide to use MXML as your main application file, then your folder structure might look like this:

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

