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
title: MXRoyale
description: Emulations of Flex UIComponent
permalink: /component-sets/mxroyale
---

# MXRoyale

Emulations of Flex UIComponent

This component set includes [Apache Royale](https://royale.apache.org/) components that reproduce the functions of some UI components many applications used in Flex. These components do not promise 100% backward compatibility and may not use the same class hierarchy as Flex.

The source code for these emulations is in the SDK at frameworks/projects/MXRoyale/src/main/royale.

**Working emulations**

This component set has working emulations in these general areas:

* AdvancedDataGrid features
* Charts
* Collections
* Containers
* Controls (dozens of them!)
* Core utilities
* Effects
* Events
* Formaters
* Graphics
* Loggers
* Managers
* Messaging
* Printing
* RPC (Remote Procedure Call)
* Skins
* States
* Styles
* Utilities
* Validators


**Stubs**

When you browse the components in the SDK, you will encounter some that seem to have no functioning code. This is a _stub_. We have created it so we can get an app migrating from Flex to compile, creating a class of the same package name and class name as the Flex component but removing all of the code and leaving a TODO note

The application including this stub can compile but the component does not do anything yet. The next task will be to add the minimal code the component needs to perform its most basic functions, and put optional and special-case functions into [beads](features/strands-and-beads) a developer can add to the component strand.

