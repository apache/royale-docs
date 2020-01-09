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

This component set includes Royale components that reproduce the functions of some UI components many applications used in Flex. These components do not promise 100% backward compatibility and may not use the same class hierarchy as Flex.

The source code for these emulations is in the SDK at frameworks/projects/MXRoyale/src/main/royale.

**Working emulations**



**Stubs**
When creating a lower-level emulation component, we first want to try to get the migrating user's app to compile. So the process is to quickly create a class of the same package name and class name as the Flex component and do one of 

1. Copy in Royale APIs (renaming them if necessary)
2. Copy in the API from the flex-sdk repo (if it will work as is) or
3. Copy in the API from the flex-sdk repo, remove all of the code and leave a TODO note

If we use the third option the result is a _stub_. The application can compile but this particular component does not do anything yet. The next task will be to add the minimal code the component need sto perform its most basic functions, and put optional and special-case functions into beads a developer can add to the component strand.



