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
---

# Features and Concepts

Key points to learn

Here are some things you may need to know to help you be more productive with Royale, although some folks get pretty far by just following the tutorial in [Create an Application](create-an-Application.html) and extending it.

## Languages

Royale uses both a declarative markup language called [MXML](Welcome/Features/MXML.html) and a scripting language called [ActionScript](Welcome/Features/AS3.html) that is like JavaScript, but with classes and interfaces and types.  This allows you to more efficiently declare the static portions of your application and write up the dynamic portions in a language where the compiler can catch more errors sooner.

## Pay as you go (PAYG)

Royale provides a variety of [component sets](./User-interface/Components.html), each tuned towards different applications requirements. The easiest one to learn and use is the Express component set. It is designed for rapid-prototyping and proof-of-concept development. You can often take code using Express into production, but because Express components are designed to be customized in MXML, as your application grows in size, you may find yourself wishing for smaller, faster components.

Royale also provides a Basic component set that is the opposite of Express.  The components are small and fast, but don't have lots of built-in customization options.  This is because Basic components are designed with a ["Pay as you go"](Welcome/Features/PAYG.html) philosophy.  Only the most common functionality is built into the component, and other options are added as plugins called Beads.  You can [read more about PAYG here](Welcome/Features/PAYG.html).

## Strands and Beads

It turns out that the Express components are really just Basic components with lots of Beads packed into them by default.  The underlying component patterns in most Royale components rely on a plug-in model.  Instead of making large component classes with lots of code baked in, each individual feature of a component is designed as its own class with an interface marking it as a "Bead", and then the component itself is called a "Strand" and Beads are placed on the Strand to compose a Royale component.  You can [read more about Strands and Beads here](Welcome/Features/Strands_and_Beads.html).

## Calling to/from external JavaScript code

Sometimes you may want your Royale application to call an external piece of JavaScript that is also hosted in your web page, or even for some extenal JavaScript from your page to call into the Royale application. In the Flex (and Flash) world, there was the possibility to use the "ExternalInterface" class to achieve this functionality. If you want this in Royale, there are some options available that you can [read about here](Welcome/Features/external-interface.html).

