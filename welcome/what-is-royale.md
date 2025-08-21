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
title: What is Royale
description: How Royale fits into the JavaScript ecosystem
permalink: /welcome/what-is-royale
---
# What is Royale?

How Royale fits into the JavaScript ecosystem

When evaluating a framework or project, the first question you might ask is how is it the same or different as "x". How does this relate to other options? This document attempts to answer those questions.

## It's a language
At the heart of [Apache Royale](https://royale.apache.org/), it's a language. Royale is the current shepherd of the ActionScript programming language. The most obvious language you would compare ActionScript to would be Typescript. The general goals of both are similar -- to add type protection for an ECMAScript language. There are differences between the approach taken by Typescript and ActionScript [which are discussed on a dedicated page](features/as3/actionscript-vs-typescript).

## It's a compiler
Royale compiles ActionScript for multiple run-times. The ActionScript compiler is an important piece of Royale. Currently, the targets are for Flash (mostly AIR applications today) and JavaScript applications. However the architecture was designed to be platform agnostic and other native platforms can be targeted in the future.

## It's a bundler
You might compare Royale to Webpack, ES Build or Parcel. Royale compiles your app both for debugging and into a single JS file for deployment.

## It's a toolbox
Royale has a huge library of functionality. Because Royale is very smart about only including in your application parts actually used, Royale is able to include a very large library of functionality without effecting application size.

## It's an ecosystem
Royale does not use npm. That's both an advantage and a disadvantage. npm give you access to a huge amount of code. That's both a blessing and a curse. If you've ever tried to stay on top of auditing npm modules and keeping them up to date, you know it's a nightmare of dependencies. Even knowing what your code depends on is very difficult with npm.

Royale tries to offset this by making a lot of functionality built in, so there's much less need for third party packages. If you do need third party libraries, you will need to include the pre-built js files explicitly.

Libraries can be included in Royale projects. These are included as SWC files. The SWC files need to be compiled using Royale, but much open source ActionScript code can be compiled with little or no work for Royale.

## It's a framework
You might compare Royale to React, Angular or Vue. Royale gives you the building blocks to create complex JavaScript applications using both declarative and imperative code. Royale differs from most frameworks in that it's very un-opinionated about **how** you build your apps. How you control state is up to you. Royale is also laser focused on performance. Read about [PAYG](features/payg) and [Beads](features/strands-and-beads) to learn more about the solutions we take to common problems.

Royale tries to be as close to "vanilla" code as possible while giving you the tools you need when and where you need them.

## It has component sets
Whether you want to style everything yourself, want themed components or want to use third party styling like MDL or Spectrum, Royale has you covered.