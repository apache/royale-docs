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
title: Features and Concepts
description: Key points to learn Apache Royale
permalink: /features-and-concepts
---

# Features and Concepts

Key points about Apache Royale

Here are some things that will help you be more productive with [Apache Royale](https://royale.apache.org/), although some folks get pretty far by just following the tutorial in [Create an Application](create-an-application) and extending it.

## AS3 and MXML Languages

Royale uses both a declarative markup language called [MXML](features/mxml) and a scripting language called [ActionScript](features/as3) that is like JavaScript, but with classes, interfaces and types. This allows you to more efficiently declare the static portions of your application and write up the dynamic portions in a language where the compiler can catch more errors sooner.

## Pay as you go (PAYG)

Royale provides a variety of [component sets](./user-interface/components.html), each tuned towards different application requirements. Components are designed with a ["Pay as you go"](features/payg) philosophy. Only the most common functionality is built into the component, and other options are added as plugins called Beads. Components designed this way use to be small and fast, and don't have lots of built-in customization options that may never be used. You can [read more about PAYG here](features/payg).

## Strands and Beads

The underlying component patterns in most Royale components rely on a plug-in model. Instead of making large component classes with lots of code baked in, each individual feature of a component is designed as its own class with an interface marking it as a "Bead", and then the component itself is called a "Strand" and Beads are placed on the Strand to compose a Royale component. You can [read more about Strands and Beads here](features/strands-and-beads).

## ExternalInterface and Externs

Sometimes you may want your Royale application to call an external piece of JavaScript that is also hosted in your web page, or even for some extenal JavaScript from your page to call into the Royale application. In the Flex (and Flash) world, there was the possibility to use the `ExternalInterface` class to achieve this functionality. If you want this in Royale, there are some options available that you can [read about here](features/external-interface).

Another option is [externs](features/externs), which use [Google Closure Compiler (GCC)](https://developers.google.com/closure/compiler){:target='_blank'} to declare that a name for a class, property or function is defined in external code and so should not be renamed when your application code is compiled. Apache Royale can use the properties of the external library, and you can even see them as options if you are using an __IDE__, with _code intelligence_ enabled. [Learn more about externs](features/externs).

## Data Binding

Data binding gives you an easy way to share data between properties and components in your application. When you bind two properties together and change the value of one, the value of the other property changes at the same time without you having to write additional code to manage it [Learn more about data binding](features/data-binding).

## View States

With View States, you can show the modules or content of your application that suits your user's permissions, what the user did most recently, or some other condition. You can assign different displays to the same part of your UI and switch quickly and smoothly between them as the user interacts with your application. [Learn more about View States](features/view-states).
