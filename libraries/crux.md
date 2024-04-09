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
title: Crux
description: An Apache Royale library based on Swiz
permalink: /libraries/crux
---

# Crux

An Apache Royale library based on Swiz Framework

The Crux framework for [Apache Royale](https://royale.apache.org/) provides:

- [Inversion of Control (IoC) and Dependency Injection (DI)](https://www.codeproject.com/articles/592372/dependency-injection-di-vs-inversion-of-control-io){:target='_blank'} with **Metadata**
- [Event handling](https://en.wikipedia.org/wiki/Event_(computing)){:target='_blank'} with **Metadata**
- Simple life cycle for asynchronous remote method invocations
- Decoupling from application code

In contrast to other major frameworks for Royale, Crux:

- Imposes no [JEE patterns](https://en.wikipedia.org/wiki/Java_Platform,_Enterprise_Edition){:target='_blank'} on your code
- No repetitive folder layouts
- No boilerplate code on your development
- Does not require you to extend framework-specific classes

> Crux represents best practices learned from the top front end developers at some of the best consulting firms in the industry, enabling Crux to be simple, lightweight, and extremely productive.

## Start here:

- **User Guide**
  - [Quick Start](libraries/crux/quickstart)
  - [Configuration](libraries/crux/configuration)
  - [IoC Container](libraries/crux/ioc-container)
  - [Dependency Injection](libraries/crux/dependency-injection)
  - View Mediator and ViewNavigator (check if we support this on Royale)
  - [Bean Life Cycle Management](libraries/crux/bean-life-cycle-management)
  - [Event Handling](libraries/crux/event-handling)
  - [Service Layer](libraries/crux/service-layer)
  - [Client Persistence](libraries/crux/client-persistence)
  - [Interfaces](libraries/crux/interfaces)
- **Advanced Topics**
  - AutowiredTestCase
  - Chaining API
  - Custom Metadata Processors
  - [Module support](libraries/crux/module-support)
  - Support for the Command pattern
  - Presentation Model
- **Examples**
  - [CruxQuickStart](https://github.com/apache/royale-asjs/tree/develop/examples/crux/CruxQuickStart){:target='_blank'}
    - This is the example showcased in the [Quick Start](libraries/crux/quickstart) above. It uses Crux and the [Jewel UI Set](component-sets/jewel).
  - [CruxQuickStartBasic](https://github.com/apache/royale-asjs/tree/develop/examples/crux/CruxQuickStartBasic){:target='_blank'}
    - This is the same example than _CruxQuickStart_ but using [Basic](component-sets/basic) intead of [Jewel](component-sets/jewel).
  - [CruxGitHubCommitLogViewer](https://github.com/apache/royale-asjs/tree/develop/examples/crux/CruxGitHubCommitLogViewer){:target='_blank'}
    - This is the same tutorial [here](create-an-application/application-tutorial), but refactored to use Crux. 
  - [TodoMVC](https://github.com/apache/royale-asjs/tree/develop/examples/crux/todomvc-jewel-crux){:target='_blank'}
    -  This is the [TodoMVC Application example](https://github.com/apache/royale-asjs/tree/develop/examples/jewel/todomvc) inspired in the [todomv.com](http://todomvc.com){:target='_blank'} site, done with [Jewel](component-sets/jewel), but refactored to use Crux.
- **Presentations**
  - ApacheCon2002: <a href="https://youtu.be/E-Fg5V5DxbY" target="_blank">Starting from a blank file (Youtube presentation)</a> - How to build a brand-new application using Royale's off-the-shelf resources including CRUX. <a href="https://apache.github.io/royale-docs/presentations/StartingFromABlankFile-ApacheCon2020.pdf" target="_blank">PDF of the slide presentation</a>

> This documentation is a migration from the official Swiz Framework docs [here](https://swizframework.jira.com/wiki/spaces/SWIZ/overview){:target='_blank'}. The original documentation was created for the original Flex framework so it's not 100% accurate for Royale.
