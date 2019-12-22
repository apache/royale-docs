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
title: Migrate from JavaScript
description: Improve your JS development experience
permalink: /create-an-application/migrate-an-existing-app/migrate-from-js
---

<!-- Based on material written for FlexJS by Peter Ent and modified by Tom Chiverton -->

# Migrate from JavaScript

Improve your JS development experience

JavaScript (JS) is a pervasive scripting language, used for everything from small animations in websites to fully-functioning applications. It is one of the three core languages of the World Wide Web, along with HTML and Cascading Style Sheets (CSS). All modern browsers, on computers and mobile devices, deploy JS by default.

Developing an application in JS generally means creating components that do specific things and then attaching components to each other via code you write. However, JS is a loosely-typed language, so you can literally attach anything to anything, sometimes with unfortunate results. You can assign a String to a variable that was expecting an Integer, and the code will have a tough time proceeding. 

JS has some 'compilers' that try to catch problems before the app user crashes into them, but once you start using Objects or low-level base classes like EventDispatcher, you can easily cause the compiler to lose track of the actual API parameters involved and not find out until too late. Often JS developers make use of libraries of functions developed and shared by other developers, only loading that code at runtime. JS verifiers have trouble keeping up when there is a problem in library code.

Most of us are familiar with furniture, toys, and other comsumables that have "some assembly required". That is true of all software languages, but some provide better guidance than others. JS offers lots of options for writing your code and sticking it together, but unless you are very attentive or very experienced, you can end up with a package has a mysterious glitch somewhere inside it that is hard to track down and fix.

Royale is also an assemble-it-yourself language. However, like the better furniture stores that provide not just the nails and screws but instructions with illustrations, Royale helps you develop in a way that minimizes errors. Semi-structured languages like ActionScript let you establish custom connectors so that the components you write can only go together in certain ways. Declarative languages like MXML provide diagrams to help you see the pieces that you are attaching and what you can expect when you stick them together. The Royale code verifier acts like an inspector, checking your work at runtime.

Many in the JS world use higher-level languages like Dart and TypeScript to reduce the chances of error in the JS code they write. Royale provides similar guardrails; it also provdes the option to use a declarative language, MXML.

If you are thinking of moving to an easier way of writing applications, compiling them into JavaScript and releasing them to the world on a wide range of platforms, Royale may be your answer.

Take Royale out for a spin!

- [Hello, world!](get-started/hello-world)
- [Create an applicaton](create-an-application)
