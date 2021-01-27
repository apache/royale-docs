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
title: PAYG
description: Pay as you Go
permalink: /features/payg
---

# PAYG

Pay as you go

_Pay as you go (PAYG)_ is a general principle for Royale. The SDK framework code (the _ActionScript_ codebase used to create Royale SDK libraries) supports incremental functionality in components. The goal is to provide components that, used just as they are, require very little memory to provide the component's most basic functions; and that can be extended to support functions that are needed sometimes, but not always. 

For example, the most basic thing a text-input component needs to do is accept text the user provides. You might have lots and lots of instances of this component in your application, and only a handful of them have to be able to support entering _passwords_ by displaying as dots the characters the user enters. For those instances only, we PAYG by extending the base component's functionality and its "cost" in memory use and impact on the application's performance.

There may be a small performance or memory cost related to implementing PAYG in the framework, but it saves a ton. Compiler options can also provide some PAYG support with no additional framework overhead.

## Philosophy

The opposite of PAYG is "_Just in Case_" code. _Just in Case_ relies heavily on class inheritance and has a lot of code that you might need only for certain components in certain circumstances. 

Classic Flex architecture took the _Just in Case_ approach and it resulted in a bloated framework. For instance, [UIComponent](https://flex.apache.org/asdoc/mx/core/UIComponent.html){:target='_blank'} is close to 15,000 lines of code, with hundreds of methods that are only needed in specific situations. Since _UIComponent_ is the base class for every UI component in Flex, every Flex application carries around every line of this code whether it needs it or not. Moreover, much of the _Just in Case_ code is called at runtime whether or not it's needed for the specific use case. This is wasteful in terms of disk space, network resources, memory and runtime performance.

PAYG takes the opposite approach. Classes only contain the code necessary for the minimum useful implementation to function. Instead of heavy reliance on inheritance, PAYG prefers composition and dependency injection. Instead of additional features being baked in, they are composed and functionality injected when needed. The theory is that this results in smaller, leaner applications. Results seem to back up this theory.

> One application which was ported from Flex4 to Royale was reduced from a total size of 1.8MB to less than 500KB of JavaScript gzipped. There is still potential in the Royale compiler to reduce the size even further. The Flash version of this application seems to be even smaller, but exact numbers are hard to determine because not all features are implemented in Flash.

## Why PAYG?

To target JavaScript, the Royale SDK and components needed to be substantially different from the legacy Flex 4 SDK and components, which were designed to compile into Flash applications and libraries. Since we had to make substantial changes throughout the code base, we took the opportunity to review how we could make general improvements to the SDK component architecture to address some common criticisms of the Flex 4 component set. One of those criticisms (the size of compiled applications) relates to the size of some of the Flex 4 base classes, which are very much 'Just in Case'. 

Implementing PAYG in Royale has the goal of maintaining the possibility of a full range of functions while keeping application size and the cost of running an app as small as possible.

## How we define default functionality

Determining whether something should be in a component's default functionality or should be added ‘as you go’ is a dynamic conversation the team engages in. You are welcome to [join in and add your insights](https://royale.apache.org/mailing-lists/){:target='_blank'}!

## What are we 'Paying' in PAYG?

'Paying' is the conscious decisions by developers to include functionality that has a measurable and substantial performance or memory impact. The ‘as you go’ implies adding ‘incremental functionality’ as needed, and only paying for what you need. In simple terms, it means that you do not pay performance and memory ‘costs’ for functionality you don’t use.

Pay as You Go is synonymous with 'Code as You Go'. Whichever term you prefer, the principle is the same: any code which is not essential for the basic component to perform its core functions should be composed elsewhere and added to instances of the component that need it. This 'elsewhere' can be a subset, an alternate set, a composable bead (see below),  etc. 

The ‘paying’ aspect of PAYG does not include _developer effort_ in the ‘payment’. For some projects that want to use a full PAYG component set, especially if they are migrating an existing Flex app to Royale, additional developer effort will be required. However, Royale provides [component sets](https://apache.github.io/royale-docs/component-sets.html){:target='_blank'} that supply most if not all of the most commonly-used components, and a growing collection of _beads_ (see below) that supply additional functions those components sometimes need.

The _Express_ component set has pre-composed components that feature combinations of functionality to suit general use cases. This reduces the time and effort required to deploy common components by including their more commonly needed functionality, helping balance ease of development against __PAYG__ benefits.

Similarly, the [Jewel](component-sets/jewel) component set is designed with PAYG in mind but tries to balance towards the usability of the framework and to not be PAYG-strict. 

## PAYG vs DRY

Another software design concept is _DRY_ (_Don't Repeat Yourself_). PAYG can sometimes be at odds with DRY. Considering that additional functionality would need to be in a different class, this can lead to multiple classes which have a lot of the same logic. Despite this, we feel that the benefits of PAYG outweigh the costs of sometimes failing to adhere to DRY.

However, we don't want to ignore DRY. Using subclasses in extended components can result in less code duplication.

> An additional technique which is used frequently in framework code is the use of utility classes or top-level functions to implement commonly-used code that is needed across different components. This utility code will only be included if it's actually used, and is only included once no matter how many times it's used. Such utility classes should be small, and each should serve a single purpose.

## How does PAYG get implemented?

### Strands and Beads

The [Strands and Beads](features/strands-and-beads) concept is a metaphor for adding extra functionality (beads) onto a component (strand). _Beads_ are the modular units of functionality that can be added to the _strand_ (base component).
 
### Compiler

Through compiler options (i.e, initialised vs. uninitiliased variables) Royale provides further PAYG capabilities.
