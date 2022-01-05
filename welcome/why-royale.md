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
title: Why Royale?
description: The advantages of using Royale
permalink: /welcome/why-royale
---
# Why Royale?

The advantages of using Royale

Let's face it: there are lots of application frameworks out there and each one claims to be the best. What does Royale give you that you don't get with other frameworks?

## Time Proven
Royale takes the best parts of Flex, which was the first major web application framework. The best minds in the field developed Flex, and one of the lead architects of Flex led the design of Royale.

## Battle Tested
Flex has run huge enterprise applications and Royale sits on that experience. Organizations are using Royale to continue to develop and run applications which were originally developed in Flex.

## Safe
Royale is backed by Apache and offers the peace of mind knowing that Apache processes govern Royale's releases.

## Javascript. Fixed!
Javascript is great, but it has a lot of weird parts. ActionScript and Royale fixes the problematic parts of Javascript:

- Unexpected type conversions are a thing of the past. Royale offers runtime type safety you will not find anywhere else.
- You don't need to be concerned with scope of "this". Functions are automatically bound to the correct scope and behave predictably.
- Inspectable types at runtime. Do you need to check for classes and interfaces at runtime? With Royale you can!
- Runtime type casting. Do you want your code to fail early if an unexpected type is used? With Royale you can.
- No more Number problems. Royale has true ints and uints. By declaring your types, you can be sure that your variables will not be converted to floating point numbers at runtime.
- Native XML support. Royale applications support the full ECMA E4X spec not generally supported by modern browsers today.

## Unopinionated
If you are using a framework, chances are you have been fighting to get the framework to do what you want. You searched Stack Overflow, only to be told, "You're doing it wrong. You need to use Framework "x" exactly like so!"

In Royale, we don't tell you how to build your applications.

  - You like OOP? Great! 
  - You like FP? Great! 
  - How should you manage your application's state? However you like! 
  - You don't like dealing with async rendering loops? Great: Royale doesn't have them. You want to control exactly how and when something is rendered? You are in the driver's seat.
  - You want to use dependency injection? Check. Don't like it? You don't need to use it.

In short, Royale gives you the tools you need and gives you some examples of what they can do, but doesn't tell you how you have to use them.

## Fast!
Most frameworks try to get as close to vanilla JavaScript as they can. In Royale we try to be _faster_ than vanilla JavaScript. In most cases Royale will _beat_ the best performance you can squeeze out of native HTML and Javascript. That's because Royale only uses the DOM when necessary and we never do any kind of DOM syncing or traversal.

## Zero configuration necessary
Out of the box, Royale will build both debug and release builds of your application. You don't need any external tools to package "tree shake" or what-have-you.

## Small and speedy deployments
Royale compiles your entire application into a single JS file, a single minified CSS file and a tiny HTML file. Your _entire deployment_ can often be smaller than 100KB. Because Royale knows a lot about your application, it can be very smart about what it includes and what it can minify.

With Royale, the need to break your app into pieces and do server-side rendering to improve performance can be a thing of the past. You can get better performance out of Royale without any of those steps.

## The kitchen sink
Royale has a lot of functionality built in that you might otherwise have to look for elsewhere.

## Open
The Royale community is truly open. We're not run by some big company with an agenda. We don't care about politics. We aren't trying to make a profit. We're just little folk like you trying to build great software. We're waiting for you to join and help us build upon the best framework on earth!
