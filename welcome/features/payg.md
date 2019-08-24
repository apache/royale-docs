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
---

# PAYG

Pay as you Go

_Pay as you go (PAYG)_ is a general principle for Royale whereby the SDK framework code (the _Actionscript_ codebase used to create Royale SDK library SWCs) supports incremental functionality in components. The goal is to provide the possibility for a lower level of performance or memory impact of applications built using the framework (compared to not applying __PAYG__ to the framework code). __PAYG__ may imply a small performance or memory cost in the framework to support its implementation, but that is recouped in its use. Some __PAYG__ aspects may also be provided by or supported by compiler options which may not have any corresponding framework overhead.

## Philosophy

To understand __PAYG__, it's very helpful to understand some background. The opposite of __PAYG__ is "_Just in Case_" code. Classic Flex architecture took this "_Just in Case_" approach and it resulted in a bloated framework. __Just in Case__ relies very heavily on class inheritance and has a lot of code that you might need for certain components. A perfect example of this is [UIComponent](https://flex.apache.org/asdoc/mx/core/UIComponent.html){:target='_blank'} which is close to 15,000 lines of code with hundreds of methods that are often not needed at all. Being that _UIComponent_ is the base class for every UI component in Flex, every application is carrying around this code whether it needs it or not. Additionally, much of this code is being run at runtime whether or not it's needed for the specific use case. This is wasteful in terms of disk space, network resources, memory and runtime performance overhead.

__PAYG__ takes the opposite approach. Classes only contain the code necessary for the minimum useful implementation to function. Instead of heavy reliance on inheritance, __PAYG__ prefers composition and dependency injection. Instead of additional features being baked in, they are composed and functionality injected when needed. The theory is that this results in smaller, leaner applications. Results seem to back up this theory.

> One application which was ported from Flex4 to Royale was reduced from a total size of 1.8MB down to less than 500KB of Javascript gzipped. There is still potential in the Royale compiler to reduce the size even further. The Flash version of this application seems to be even smaller, but exact numbers are hard to determine because not all features are implemented in Flash.

## What is 'Paying' in PAYG

'Paying' is defined as conscious decisions by developers to include functionality that has a measurable and substantial performance or memory impact. The ‘as you go’ implies ‘incremental functionality’. In simple terms, it means that you do not include performance and memory ‘cost’ for functionality you don’t use.

The word 'Paying' can be replaced by the word 'Code'. Pay as You Go is synonymous with 'Code as You Go'. That is (in general), any code which is not essential for the functioning of the basic component should be composed to be used "as you go" elsewhere. This elsewhere can be a subset, an alternate set, a composable bead etc. The point is that "just in case" code should not be included in the basic minimal useful implementation. It should be included only when you want it, or opt in to "just in case" code.

The ‘paying’ aspect of PAYG does not include 'developer effort' as ‘payment’ or ‘cost’. This means that for some projects using a full __PAYG__ component set, additional developer effort will be required, however the Royale project team is working to reduce this by composing sets of general purpose components that include ‘general purpose’ functionality (See [Doesn’t supporting PAYG have its own cost?](welcome/features/payg.html#doesnt-supporting-payg-have-its-own-cost) below).

## How is ‘measurable and substantial’ defined to determine thresholds for default functionality?

Determining whether something has merit for inclusion in default functionality or is categorised into ‘as you go’ is something that has generated discussions in the mailing lists and has resulted in disparate views. Perhaps part of the reason for this is a lack of clarity and/or consensus as to whether ‘paying’ includes developer effort or not (see What is [Paying](welcome/features/payg.html#what-is-paying-in-payg) above).

## Why PAYG?

To target Javascript, the Royale SDK and components needed to be substantially different to the legacy Flex 4 SDK which is SWF-only. Given this need to make large changes, the opportunity was also taken to review general improvements to the SDK component architecture to address some common criticisms of the Flex 4 component set. One of those criticisms (the size of compiled applications) relates to the size of some of the Flex 4 base classes which, in simple terms, is the opposite of PAYG. 

Implementing __PAYG__ in Royale has the goal of maintaining the possibility of a full range of functionality, but making it more incremental/opt-in.

## Doesn’t supporting PAYG have its own cost?

### Performance

Performance cuts both ways. __PAYG__ may contribute to performance costs, because there is some overhead in supporting a runtime based composition model. On the other hand, __"Just in Case"__ code is not being run, so that more than likely offsets the overhead. Moreover, the general principle is that establishing the ability to compose functionality (especially via MXML) is worth the overhead. For features that are opt-in via the compiler, these features may not have an extra framework cost.

### Developer Effort

Because there can be extra effort to compose incremental functionality for common use cases, it would likely result in extra developer effort being required if the developer was using a full __PAYG__ approach to development on every project.

For this reason, the __Express__ component set exists which has pre-composed components that feature combinations of functionality to suit more general use cases. The intention behind this is to reduce the time and effort required in the use of common components by including the more commonly needed functionality. The vision is that there should be a collection of component sets which compose the functionality required for specific types of applications. This can help balance ease of development against __PAYG__ benefits.

The same can be applied to [Jewel](component-sets/jewel.html) component set that is designed with __PAYG__ in mind but tries to balance towards the usability of the framework and to not be so strict. 

## PAYG vs DRY

Another software design concept is __DRY__ (_Don't Repeat Yourself_). __PAYG__ can sometimes be at odds with __DRY__. Considering that additional functionality would need to be in a different class, this can lead to code repeat and multiple classes which have a lot of the same logic.

Despite this, we feel that the benefits of __PAYG__ out way the costs of sometimes failing to adhere to __DRY__.

However, we don't want to ignore __DRY__ and it's worth noting that it's not always an issue, and the cost can be mitigated. Many of these cases are simply alternate implementations of the same type of component. When picking the component set, the minimal usable implementation should be selected. If the larger implementation is needed, and is used consistently across the application, this code duplication might never make it into the end application. Additionally, use of subclasses in extended components can result in less code duplication.

> An additional technique which is used frequently in framework code is the use of utility classes or top level functions to implement commonly used code that is needed across different components. This utility code will only be included if it's actually used, and only be included once no matter how many times it's used. Utility code should be small and serve a single purpose.

## How does PAYG get implemented?

### Strands and Beads

The [Strands and Beads](welcome/features/strands-and-beads.html) concept is a metaphor for adding extra functionality (beads) onto a component (strand). __Beads__ represent the modular units of functionality that can be selected and composed together to configure functionality added to the __Strand__ (base component). Component sets such as ‘Express’ include more general functionality which may into reduce developer effort for the general case of application development.
 
### Compiler

Through compiler options (i.e, initialised vs. uninitiliased variables) Royale is providing __PAYG__ capabilities too.

