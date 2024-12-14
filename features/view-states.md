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
title: View States
description: State-related management of the UI
permalink: /features/view-states
---

# View States

State-related management of the UI

The View States feature is a way of putting different filters over parts of your application so that different things appear depending on what the app is doing, what permissions the user has, what the user just did, or some other condition. You create a series of “states” and associate components of your application with one or more of the states. When the current state of the application is "loggedIn", for example, the user only sees components and containers set to be visible in the "loggedIn" state. 

Learn how to use View States in your app:

* [A tutorial on View States](https://royale.apache.org/blog/using-view-states-to-show-or-hide-content){:target='_blank'} on the Royale blog.
* The [Tour de Jewel](https://royale.apache.org/tourdejewel){:target='_blank'} page, which has a wealth of examples of using Royale's [Jewel component set](/component-sets/jewel), has an interactive demonstration of using View States with both "includeIn" and dot notation, with downloadable code you can adapt to your app's needs.
