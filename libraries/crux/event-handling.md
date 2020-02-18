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
title: Event Handling
description: Event Handling with Crux
permalink: /libraries/crux/event-handling
---

# Event Handling

Learn about event handling in Crux

Page Contents:

- [Dispatching Events](libraries/crux/event-handling.html#dispatching-events)
- [Handling Events with [EventHandler]](libraries/crux/event-handling.html#eventhandler)
  - [Event Handling Using Class and Constant Names](libraries/crux/event-handling.html#eventhandler-class-const-names)
  - [Event Handling Using Event Type Value](libraries/crux/event-handling.html#eventhandler-event-type-value)
  - [[EventHandler] tag options](libraries/crux/event-handling.html#tag-options)
    - [properties attribute](libraries/crux/event-handling.html#properties-attribute)
    - [Other attributes](libraries/crux/event-handling.html#other-attributes)
  - [Handling Multiple Events from a Single Method](libraries/crux/event-handling.html#multiple-events-single-method)

Crux offers features to assist with both the dispatching and handling of events within an application. The following sections explain these features in detail.

## Dispatching Events {#dispatching-events}

Application events typically fall into two categories: those dispatched from children of visual objects, and those dispatched from non-UI objects. Crux makes it easy to handle both kinds of events in a standard way.

Dispatching events from UI components is done using the standard `dispatchEvent()` method that `UIBase` provides. If you dispatch events that bubble, Crux can listen for these events in the root container and invoke event handlers to handle these events.

Dispatching events from non-UI component beans is done using an event dispatcher provided by Crux. There are two ways to instruct Crux to inject a dispatcher. The most common way is to use the `[Dispatcher]` metadata tag. Crux will automatically inject the dispatcher into a public property decorated with this metadata.

```as3
[Dispatcher]
public var dispatcher:IEventDispatcher;
```

The other option is to implement the Crux `IDispatcherAware` interface. Since implementing this interface creates a direct dependency on the Crux framework, it should be avoided if possible.

Once the dispatcher is injected, you can use it to dispatch events that can be handled using metadata-based event handlers. Event handlers are described in the next section.

> In situations where you have two or more Crux instances in a parent/child relationship, you can exercise some additional control over how events are dispatched and handled. See the section on [Module support](libraries/crux/module-support) for more information.

## Handling Events with [EventHandler] {#eventhandler}

Crux handles application events using the `[EventHandler]` metadata tag. `[EventHandler]` provides several benefits:

- You no longer need to manually declare event listeners in your code. Crux will transparently create an event listener for the specified event when the bean is created, and will invoke the target method whenever that event is captured. Further, Crux will automatically remove the event listener when the bean is destroyed or removed from the display list.
- You no longer need event-specific handler methods to respond to events. `[EventHandler]` methods can be declared without specifying an Event object as a method argument (see below). As a result, you can easily invoke these methods yourself, outside the context of responding to an event, in addition to having Crux invoke them automatically.
- A single method can easily respond to multiple event types.
- Because the methods are annotated with metadata, it is possible to introspect a class to determine what events it will respond to. This is not possible when the code manually creates event listeners.

In order for an event to be handled, it must be dispatched from the Crux dispatcher (as shown above) or be a bubbling event. `[EventHandler]` tags are defined on methods and must specify the event to be handled. The event can be specified using the string value of the event's type property, or by using the class and constant names of the event.

> Methods decorated with `[EventHandler]` must be public, since the runtimes provides no mechanism for invoking non-public methods directly.

### Event Handling Using Class and Constant Names {#eventhandler-class-const-names}

If you wish to use event constants in your `[EventHandler]` metadata, this is the required approach. There are two reasons Crux requires this. First, it allows Crux can verify the event class exists and has a constant with the provided name. Second, it allows Crux to process different events that have the same string literal type by matching on the class and constant name instead of the value. This syntax assumes you have a subclass of `Event` named `UserEvent`, and that you have added `com.foo.events` to the `eventPackages` property of `CruxConfig`.

```as3
[EventHandler( event="UserEvent.ADD_USER" )]
public function handleAddUserEvent( event:UserEvent ):void
{
    // do stuff
}
```

If you do not specify any `eventPackages`, you can provide the fully qualified path in the `[EventHandler]` tag:

```as3
[EventHandler( event="com.foo.events.UserEvent.ADD_USER" )]
public function handleAddUserEvent( event:UserEvent ):void
{
    // do stuff
}
```

### Event Handling Using Event Type Value {#eventhandler-event-type-value}

Good for quick prototyping but lacks error checking and could suffer from collisions. Not recommended.

```as3
[EventHandler( event="addUser" )]
public function handleAddUserEvent( event:UserEvent ):void
{
    // do stuff
}
```

### [EventHandler] tag options {#tag-options}

The examples above show methods that take the target event as an argument, but in some cases you don't need the event passed to your method. Crux will intelligently examine the signature of your method and call it without parameters if that is how it's defined.

```as3
[EventHandler( event="UserEvent.ADD_USER" )]
public function handleAddUserEvent():void
{
    // do stuff
}
```

#### properties attribute {#properties-attribute}

You can also specify a comma delimited list of property names in the tag to have the matching properties pulled off of the event and passed into your method. This can be useful for allowing methods to be defined in a more semantic manner to mask the fact that they are event listeners.

You can use property chains as well, i.e. `user.permissions`.

```as3
[EventHandler( event="UserEvent.ADD_USER", properties="user" )]
public function addUser( user:User ):void
{
    // do stuff
}
```

#### Other attributes {#other-attributes}

Since `[EventHandler]` causes Crux to create an event listener behind the scenes, it also supports some related attributes. `useCapture`, `stopPropagation` and `stopImmediatePropagation` are all supported, and Crux will handle their implementation for you. `useCapture` map directly to the `useCapture` parameter of the resulting listener. Setting `stopPropagation` or `stopImmediatePropagation` to `true` will cause Crux to automatically call the corresponding methods on the event after your method executes.

### Handling Multiple Events from a Single Method {#multiple-events-single-method}

It is possible to handle multiple events using a single method:

```as3
[EventHandler( event="UserEvent.ADD_USER", properties="user" )]
[EventHandler( event="UserEvent.EDIT_USER", properties="user" )]
[EventHandler( event="UserEvent.DELETE_USER", properties="user" )]
public function handleUserEvents( user:User ):void
{
    // do stuff
}
```

Additionally, you can handle any event type of a given event using a wildcard:

```as3
[EventHandler( event="UserEvent.*", properties="user" )]
public function handleUserEvents( user:User ):void
{
    // do stuff
}
```