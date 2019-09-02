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
title: Making a production version
description: Releasing an application for consumers
---

# Making a production version

Releasing an application for consumers

The version in the "js-debug" folder is considered a "debug version" or "development version".  If you looked at all of the files in the folder or copied them to a web server, you probably noticed there are quite a few, and that each takes time to load.

These versions are designed to be more easily debugged. Each source file has an equivalent .js file with nice, readable variable and function names. If the files are small enough and fast enough, it is perfectly fine to deploy the development version.

A production version will combine just about all of the .js into a single .js file, renaming variables and function names from things like "Application" to just "aa". This is done using the [Google Closure Compiler (GCC)](https://developers.google.com/closure/compiler/){:target='_blank'} and the results are easier to manage (fewer files to copy) and also should load more quickly (because there are fewer requests for files and smaller total file sizes).

If you are using an IDE, it probably provides an option for creating a production version. On the command line, to create a production version, don't set debug=true. The compiler will still produce the js-debug folder, but it then will pass it to the Google Closure Compiler that will generate a production or "release" version in a "js-release" folder. 

The build process will take longer as the Google compiler crunches through all of the files.  There may be additional warnings, and hopefully, no errors.  If there is an error, then the production version will probably not run.

On the command line, create a production version by running:

`<path to Royale SDK>/royale-asjs/js/bin/mxmlc GitHubCommitsViewer.mxml`

If you've used [NPM](https://www.npmjs.com/){:target='_blank'} to install Royale, you can just run:

`mxmlc GitHubCommitsViewer.mxml`

Then if your browser worked when you viewed the application in the js-debug folder, you can review the production version the same way in the js-release folder; or you can copy the js-release folder to your webserver.

You will probably not see any rows of commits.  And if you look in the console, you may see an error that looks like:

`TypeError: undefined is not an object (evaluating 'e.Vf.Qf')`

Why is the production version not working? Because as the Google Closure Compiler renamed variables, it also renamed variables in the code that fetches fields from the data.

How do you prevent certain variables from being renamed?  One way is by not using as many plain objects, especially when those objects come from an external source. If a plain object is used entirely internally, then the Google Closure Compiler can rename all references to a property like "message" to just "mm". Google doesn't know or have a way to know that the objects in this tutorial are coming from a server.  

There is more than one way to keep Google Closure Compiler from renaming variables, but not using plain objects has other advantages as we'll see in the next section.

{:align="center"}
[Previous Page](create-an-application/application-tutorial/security.html) \| [Next Page](create-an-application/application-tutorial/value-objects.html)
