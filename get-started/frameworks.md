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
title: Frameworks
description: Sets of code libraries availables in Royale
permalink: /get-started/frameworks
---

# Frameworks

Sets of code libraries availables in Royale

A framework is a set of code that provides support for application development by offering templates, components and examples. Developers using Adobe and Apache Flex benefitted from a number of frameworks, including: Tide, Swiz, Parsley, Cairngorm, PureMVC, DropAS3, Fabrication, Mate, and RobotLegs.

[Apache Royale](https://royale.apache.org/) provides its own framework for making simple, small and fast applications, but also offers support for deploying additional Royale frameworks and using popular JavaScript frameworks.

## Apache Royale frameworks

The first Royale framework in development is [Crux](libraries/crux), based on Swiz for Flex. It proposes to provide:

- Inversion of Control (IOC) / Dependency Injection (DI) with metadata
- Event handling (metadata)
- Simple life cycle for asynchronous remote method invocations
- Decoupling from application code

Documentation for Crux will be available soon.


## Apache Royale Component Sets

Apache Royale supports its own [component sets](component-sets) of controls, options for grouping controls, and other elements designed to help developers get the most of the technology.

- [Basic](component-sets/basic) is the most smallest, fastest and most PAYG set of components possible in Royale, and is used by other sets like Jewel as their base.

- [Jewel](component-sets/jewel) is focused in look and feel and new practices present in modern development like responsivness and multiplatform support. Jewel supports Themes and diferent kind of desktop and mobile devices.

Why would you use a third-party framework with Royale? Because you like the look and feel of that framework's user interface components but want to use ActionScript to handle the business logic and/or use MXML to set up the UI.


### Other Component Sets

These component sets are created under the Royale umbrella, but use or wrap existing external libraries or frameworks. Royale supports (to varying degrees):

- [Material Design Lite](https://getmdl.io){:target='_blank'} Most, if not all, components are available.

- [JQuery UI](https://jqueryui.com){:target='_blank'} Only a few components are available. Volunteers are needed to support more components. Note that this does not mean that you write actual JQuery queries in your application source code; it just means that you can use the user interface controls to get the same user experience as JQuery apps offer.

- [CreateJS](https://www.createjs.com){:target='_blank'} Only a few components are available. Volunteers are needed to support more components.

Many other JavaScript frameworks could be made to work with Royale if they support dynamic instantiation of components. All it takes is volunteers to make it happen.
