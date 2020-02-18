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
title: Bean Life Cycle Management
description: Bean Life Cycle Management with Crux
permalink: /libraries/crux/bean-life-cycle-management
---

# Bean Life Cycle Management

Learn about the bean life cycle

Page Contents:

* [Manually Creating and Destroying Beans](libraries/crux/bean-life-cycle-management.html#create-destroy-beans)
* [[PostConstruct] and [PreDestroy]](libraries/crux/bean-life-cycle-management.html#postconstruct-predestroy)
<!-- 
CruxConfig Options libraries/crux/bean-life-cycle-management.html#cruxconfig-options
Crux and Royale Life Cycle Steps libraries/crux/bean-life-cycle-management.html#life-cycle-steps
-->

## Manually Creating and Destroying Beans {#create-destroy-beans}

Crux provides an event-based mechanism to create or destroy beans. To create a new bean, you can dispatch the `BeanEvent.SET_UP_BEAN` or `BeanEvent.ADD_BEAN` events:

```as3
[Dispatcher]
public var dispatcher : IEventDispatcher;
 
private function createNewBean() : void
{
    userModel : UserModel = new UserModel();
     
    // Crux will create a bean for the userModel, and process any metadata in it.
    dispatcher.dispatchEvent( new BeanEvent( BeanEvent.SET_UP_BEAN, userModel ) );
}
```

Both `SET_UP_BEAN` and `ADD_BEAN` will process the target object as a bean. The difference between these events is that `ADD_BEAN` will also add the bean as a singleton to the `BeanFactory` cache, while `SET_UP_BEAN` does not add the new bean to the cache.

Similarly, to destroy a bean, you dispach the `BeanEvent.TEAR_DOWN_BEAN` or `BeanEvent.REMOVE_BEAN` events:

```as3
private function destroyBean() : void
{
    // Crux will destroy the userModel bean, clean up any injected objects, and delete any injection bindings.
    dispatcher.dispatchEvent( new BeanEvent( BeanEvent.TEAR_DOWN_BEAN, userModel ) );
}
```

The tear down events mirror the set up events discussed previously: `TEAR_DOWN_BEAN` cleans up the target by removing injections, event handlers, etc., while `REMOVE_BEAN` cleans up the bean as well as removing it from the singleton cache in the BeanFactory.

> Since `BeanEvent` is a **bubbling event**, you can dispatch it from a view. If you dispatch them from non-view beans, be sure you use an injected dispatcher so that Crux can handle the event.

If necessary, you can directly call the `setUpBean()` and `tearDownBean()` methods on the `BeanFactory`. Since these methods both take a `Bean` instance as an argument, you can use the `createBeanForSource()` method on the `BeanFactory` to generate a `Bean` instance that you can then pass into the set up and tear down methods. However, in general the event-based approach to creating and tearing down beans should be the preferred approach.

## [PostConstruct] and [PreDestroy] {#postconstruct-predestroy}

Crux provides two metadata tags which allow you to trigger methods when any bean is set up or torn down. You can decorate a public method with `[PostConstruct]` and that method will be invoked by the framework after the bean has been set up, had dependencies injected, and had mediators created. For example:

```as3
package org.apache.royale.quickcrux.controller
{
    import org.apache.royale.quickcrux.service.UserService;
 
    public class UserController
    {
        [Inject]
        public var userService : UserService;
 
        /**
         * [PostConstruct] methods are invoked after all dependencies are injected.
         */
        [PostConstruct]
        public function createDefaultUser() : void
        {
            userService.loadDefaultUser();
        }
    }
}
```

Similarly, a public method decorated with `[PreDestroy]` will be called when a bean is destroyed by Crux. This would happen if a UI component is removed from the stage, or a module is unloaded.

```as3
package org.apache.royale.quickcrux.controller
{
    import org.apache.royale.quickcrux.service.UserService;
 
    public class UserController
    {
        [Inject]
        public var userService : UserService;
 
        /**
         * [PreDestroy] methods are invoked when a bean is destroyed.
         */
        [PreDestroy]
        public function clearPollingTimer() : void
        {
            userService.stopPolling();
        }
    }
}
```

<!--
## CruxConfig Options {#cruxconfig-options}

Six configuration options are available in the `CruxConfig` object to specify how UI components are handled by the framework. These are setUpEventType, setUpEventPhase, setUpEventPriority, and the corresponding tearDownEventType, tearDownEventPhase, and tearDownEventPriority. Normally, you can leave these at their default values. But if you need to, you can modify these to alter how Crux creates and destroys beans that are UI components.

The default setUpEventType is "addedToStage". This means that whenever a UI component is added to the stage, Crux will inspect the component and process any metadata it finds. Any dependency injections and event mediators will happen at this time. As mentioned, you may change this value if "addedToStage" is not ideal for your situation. "creationComplete" is another commonly used setUpEventType.

Be careful if you use an event type that occurs early in the Royale component life cycle, such as "preinitialize", since child components have not been created yet.

At the other end of the bean life cycle, the default tearDownEventType is "removedFromStage". This means that when a UI component is removed from the stage, Crux will perform clean up activities such as removing event mediators.

If you require even more fine-grained control, you can specify alternative values for the phase and priority used for the set up and tear down of beans. Typically, these won't need to be changed, but the options are there in case they are needed.

You can also use the ISetUpValidator and ITearDownValidator interfaces with UI components to control whether set up or tear down are allowed.
-->

<!-- 
## Crux and Royale Life Cycle Steps {#life-cycle-steps}

> Note that the Royale component lifecycle events shown in all of these tables outline the most common order, but that it is not universal. For example, when a Module is loaded, it will dispatch addedToStage before dispatching creationComplete. These inconsistencies are simply how the Royale SDK operates.

The following table shows the steps that Royale and Crux will go through on application startup:

Type
Step
Royale
Preinitialize event
Crux
dispatcher set
Crux
Crux created event
Crux
domain set
Crux
Global dispatcher set
Crux
Processors initialized
Crux
Bean factory initialized
Crux
setUpEvent and tearDownEvent values set from CruxConfig
Crux
Beans defined in the BeanProvider(s) are processed
Crux
(per bean) beanFactory.setUpBean()
Crux
(per bean) [Inject] processed
Crux
(per bean) [EventHandler] processed
Crux
(per bean) [Dispatcher] processed
Crux
(per bean) Default custom metadata processed
Crux
(per bean) [PostConstruct] processed
Royale
Initialize event
Royale
Creation complete event
Royale
Added to stage event
Royale
Display objects in the display list are processed (see table below)
Royale
Application complete event
Royale
Update complete event

The following table shows the steps that Royale and Crux will go through when a new display object is set up:
Type
Step
Royale
Invalidation
Royale
Property bindings
Royale
Preinitialize
Royale
Create children
Royale
Initialize event
Royale
Commit properties
Royale
Resize
Royale
Render
Royale
Measure
Royale
Set actual size
Royale
Update display list
Royale
Creation complete event
Royale
Added event
Royale
Added to stage event
Crux
beanFactory.setUpBean()
Crux
[Inject] processed
Crux
[EventHandler] processed
Crux
[Dispatcher] processed
Crux
Default custom metadata processed
Crux
[PostConstruct] processed
Crux
[ViewAdded] processed
Royale
Update complete event

The following table shows the steps that Royale and Crux will go through when a display object is torn down:

Type
Step
Royale
Removed event
Royale
Removed from stage event
Crux
[PreDestroy] processed
Crux
[Inject] tear down
Crux
[EventHandler] tear down
Crux
[Dispatcher] tear down
Crux
Default custom metadata tear down
Crux
[ViewRemoved] processed -->
