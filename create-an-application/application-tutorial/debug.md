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
title: Debug the application
description: Find and resolve defects or problems within a Royale application.
permalink: /create-an-application/application-tutorial/debug
---

# Debug the application

Find and resolve defects or problems within a Royale application.

If the application built and showed a set of columns but no commit data, then you are probably running a browser that has a tighter security model than some other browsers.

> Some browsers won't let an application access data from another domain without permission.

But to verify that, or whenever something goes wrong in your application, the first step is to open the console window for your browser.  How to do that depends on the browser, but basically, the output JavaScript is going to be executed until it throws an *"uncaught exception"* and code that was supposed to run after that won't and that will result in lots of things not working.

In one browser, the console said:

```
Failed to load file:///.../bin/js-debug/project.json: Cross origin requests are only
        supported for protocol schemes: http, data, chrome, chrome-extension, https.
```

Because I simply opened the file from my computer's file viewer in the browser, the browser opened it under the `file:///` protocol and wouldn't allow access from my computer to GitHub.

So, to do further testing you will need to set up a web server for the application or copy the application to a web server and run it from there. If you look in the `js-debug` folder, you will find a lot of files you have to copy. You can't just copy the `index.html` file.

Back to the topic of debugging for a moment. Most browsers also have debuggers with breakpoints. Your application `.mxml` and `.as` files have each been turned into a `.js` file that the browser will let you set breakpoints in and step through. Some IDEs support the ability to see your `.mxml` and `.as` files in the debugger.

> if you compiled your application with [sourcemaps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps){:target='_blank'} using `-source-map=true` compiler option, the Royale compiler will generate source maps for each `.js` file and you'll see a `.js.map` at the same level.

Anyway, to get this application to access GitHub, we have to make the application available on a web server and learn a bit about security.

{:align="center"}
[Previous Page](create-an-application/application-tutorial/deploy) \| [Next Page](create-an-application/application-tutorial/security)

