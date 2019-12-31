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
title: Frameworks and Libraries
description: pre-written sets of code which allows for easier development of Royale-based applications
permalink: /frameworks-and-libraries
---

# Frameworks and Libraries

Pre-written sets of code which allows for easier development of Royale-based applications.

Frameworks provide reliable templates to help you develop complex projects more easily and sustainably. Libraries are generally collections of modules and functions that focus on a particular task or theme--you might find a library to help you with scientific calculations, and another library for manipulating graphics.

## Frameworks
Apache Royale itself is a framework. It can play well with other frameworks to help simplify development, especially when many people are working on the same project.

### Designed for Apache Royale:

* [Crux](libraries/crux) is a library based on Swiz. Swiz is a framework that simplifies applications and gives you Inversion of Control/Dependency Injection, Event handling, new Metadatas, simplified life cycle for asynchronous remote method invocations and many more. Swiz was developed specifically for ActionScript and Flex.

### Third party frameworks

* [PureMVC](https://github.com/PureMVC/puremvc-as3-multicore-framework/wiki){:target='_blank'} is a lightweight framework for creating applications based upon the classic Model-View-Controller design meta-pattern. Is part of [The PureMVC Framework](https://puremvc.org){:target='_blank'} that implements the same library in many other popular languages and technologies.

## Libraries

* There are a large number of [ActionScript3](/features/as3) libraries that should "just work" when you import them into your Royale application. Others may need adjustment if they presume that your application will run on Flash, not in a modern browser.
* Use the [ExternalInterface](/features/external-interface) class to connect with and use external JavaScript libraries in your Royale project.
* An even more robust method for connecting with and using external JavaScript libraries is [externs](/features/externs).

See a working example at [Using external JavaScript libraries in Apache Royale](https://royale.apache.org/using-external-javascript-libraries-in-apache-royale/){:target="_blank"}.

_We will add here information about specific libraries that work well with Royale as we run into them._



