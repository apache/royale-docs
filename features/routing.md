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

There are two types of routing. Routing can be completely within the browser and in that case, the routing is handled in the portion of the URL after the hash (`#`). This is called "hash routing" or `HashRouter`. A more complex form of routing can be used which is indistinguishable from separate path-based web pages. This (for lack of a better term) is called browser routing `BrowserRouter`. To use browser routing, your server must be setup to support this.

`HashRouter` can be used with, or without "hash-bangs" A hash-bang (`#!`) is a special notation to search engines that the hash should be treated as a page to be indexed by the search engine. Regular hashes will work the same, but will generally not be searchable. Hash-bangs can be enabled or disabled using the `useHashBang` property.

`BrowserRouter` requires a `basePath` to function correctly. This is the path relative to the domain where the application is loaded. Anything below that path will be considered a "routing" path. The base path needs to match the settings on the server. There are many guides on the web on how to setup your server [here's one](https://www.digitalocean.com/community/tutorials/react-react-router-ssr). Any instructions for setting up a particular server to work with Angular or React (or most other modern js framework) routing should work fine.

On the most basic level, routers (whether hash based or path browser based) can be used by manually reacting to router state changes.
````
<js:HashRouter id="router" stateChange="hashChanged()"/>
````

````
<js:BrowserRouter id="router" stateChange="hashChanged()"/>
````

In the above examples, any time the route changes, the `stateChanged` function will be called.

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

`Router`s and `RouteToState` can be declared on and for more than one component, so state can be changed and synced across multiple components with ease.

Another example which routes to components:
````
<js:Router localId="router">
    <js:RouteToComponent component="{footer}"/>
    <js:RouteTitleLookup lookup="{getTitleLookup()}"/>
</js:Router>
````

The currently supported beads are the following:
### `RouteToComponent`
### `RouteToParameters`
### `RouteToState`
### `SetRouteTitle`
### `PathRouteBead`

*Instructions and sample code will appear here soon to show how you can map URL parameters to different initial values in the application, and vice versa.*
