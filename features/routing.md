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
title: Routing
description: Map URL parameters to different initial values in the app
permalink: /features/routing
---
# Routing

Map URL parameters to different initial values in the app, and vice versa

_this page is not complete_

## Basic Router
````
<js:Router id="router" stateChange="hashChanged()"/>
````
In the above example, any time the route changes, the `stateChanged` function will be called.

The state of the router can likewise be changed directly by modifying the `router.routeState` and calling `router.setState()` `router.renderState()` is a similar method, but it will dispatch the `stateChanged` event as well and cause any attached beads to react to the state change.

## Router Beads
The full power of the Router becomes apparent when you use beads. Router can automatically sync the route state with the component's state. It can change which component is shown by creating and removing components. It can handle parameters, etc. Here are some examples:
````
<js:Router localId="router">
    <js:RouteToState component="{footer}"/>
    <js:RouteTitleLookup lookup="{getTitleLookup()}"/>
</js:Router>
````

In this example, the router syncs the state of the footer with the route path. The RouteTitleLookup allows changing the window title based on the state. The `lookup` property is an object whose keys are the state names and the values are the corresponding titles.

Routers and RouteTotState can be declared on and for more than one component, so state can be changed and synced across multiple components with ease.

Another example which routes to components: (in progress)
````
<js:Router localId="router">
    <js:RouteToComponent component="{footer}"/>
    <js:RouteTitleLookup lookup="{getTitleLookup()}"/>
</js:Router>
````

*Instructions and sample code will appear here soon to show how you can map URL parameters to different initial values in the application, and vice versa.*
