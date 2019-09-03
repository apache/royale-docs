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
title: Application tutorial
description: A complete tutorial on how to build a simple Royale application
permalink: /create-an-application/application-tutorial
---

# GitHub Commit Log Application Tutorial

A complete tutorial on how to build a simple Royale application

This tutorial will take you through building an app that displays the commit logs for the Royale project by connecting to the [GitHub](https://github.com){:target='_blank'} servers.

At the end of this tutorial we'll get the following:

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="350" 
src="assets/application-tutorial/index.html"></iframe>

> This example uses [Basic](component-sets/basic) components to build the interface. This components are build with very basic look and feel. For a more advanced set with look and feel you should use instead [Jewel](component-sets/jewel) or **MDL** sets

The steps in this tutorial start with a blank file and walk you through what to add and why. Or you can get the complete source [here](https://github.com/apache/royale-asjs/blob/develop/examples/express/GitHubCommitLogViewer){:target='_blank'}.

> Note that Royale examples are set up to build with [Apache Maven](https://maven.apache.org){:target='_blank'} so the folder structure reflects that. There are other ways to organize your code.

The first six segments will result in a functional application.

1. [The Main Application File](create-an-application/application-tutorial/main) This segment starts filling in the main application file.

2. [Data Model](create-an-application/application-tutorial/data-model) This segment adds the code that manages the data in the application, including network access to GitHub.

3. [View (User Interface)](create-an-application/application-tutorial/view) This segment builds out the initial user interface.

4. [Controller](create-an-application/application-tutorial/controller) This segment hooks up the user interface to code that responds to the user's interactions.

5. [Build](create-an-application/application-tutorial/build) This segment gets the code to compile.

6. [Run](create-an-application/application-tutorial/deploy) This segment discusses how to view the results.

The next four segments will discuss further improvements needed to make a production-ready version.

7. [Debugging](create-an-application/application-tutorial/debug) This segment introduces a couple of techniques for figuring out why your app isn't working as expected.

8. [Security](create-an-application/application-tutorial/security) This segment discusses how to deal with network access to other domains.

9. [Production](create-an-application/application-tutorial/production) This segment discusses the differences between a development version and a production version of an app.

10. [Value Objects](create-an-application/application-tutorial/value-objects) This segment explains how Value Objects (Data Classes) are useful in development and production.

The remaining segments will discuss further improvements needed to add additional common functionality. (*Note: These pages are not yet complete.*)

11. [Localization](create-an-application/application-tutorial/locales) This segment adds the ability to show the user-interface prompts in different languages.

12. [Filters](create-an-application/application-tutorial/filters) This segment adds the ability to filter what commits are shown.

13. [Local Storage](create-an-application/application-tutorial/local-storage) This segment shows how to store information in a cookie or equivalent in order to retain some of the state of the app between runs.

14. [Routing](create-an-application/application-tutorial/routing) This segment shows how to map URL parameters to different initial values in the application, and _vice versa_.

This is going to be fun!
