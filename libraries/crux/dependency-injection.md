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
title: Dependency Injection
description: Crux Dependency Injection
permalink: /libraries/crux/dependency-injection
---

# Crux Dependency Injection

Crux Dependency Injection

Page Contents:

* [Dependency Injection Overview](libraries/crux/dependency-injection#overview)
* [Inject by type](libraries/crux/dependency-injection#inject-by-type)
* [Inject by name](libraries/crux/dependency-injection#inject-by-name)
* [Inject bean property](libraries/crux/dependency-injection#inject-bean-property)
* [Two way bindings](libraries/crux/dependency-injection#two-way-bindings)
* [Setter injection](libraries/crux/dependency-injection#setter-injection)
* [Injection destination](libraries/crux/dependency-injection#injection-destination)

## Dependency Injection Overview {#overview}

The **IoC Container** of Crux is the `BeanProvider` class. Any beans defined in a registered `BeanProvider` can be injected into other registered beans or into views added to the display list.

Defining an injection target is done using the `[Inject]` metadata tag. Common injection scenarios include the following:

- Inject Model into View
- Inject Model into Controller
- Inject Delegate into Controller
- Inject Service into Delegate

Due to restrictions imposed by runtimes, Crux cannot inject into `private`, `protected` or `internal` members.

By default, injections in view components happen during the `ADDED_TO_STAGE` event. <!--This behavior can be modified by changing the Crux configuration.--> It is important to understand that this means that injections occur after the <!--CREATION_COMPLETE-->`initComplete` event. If you need to trigger logic during creation that depends on injections, use a `[PostConstruct]` method.

> Note: `ADDED_TO_STAGE` is a SWF event. In __Javascript__ you need to add a bead to your Application beads called `JSStageEvents` to simulated stage events like `ADDED_TO_STAGE` or 'REMOVED_FROM_STAGE`

## Inject by type {#inject-by-type}

If you define exactly one bean of a given type you can inject it into a matching destination with a plain `[Inject]` tag. Note this also supports injecting a concrete implementation of an interface to which the destination is typed. In other words, if a property decorated with `[Inject]` is of type `IUserService`, Crux will correctly inject a bean implementing that interface, such as `UserService` or `MockUserService`.

```as3
[Inject]
public var model:IUserModel;
```

> **Best Practice**. You should inject by type whenever possible. It avoids reliance on string based names, which can lead to run time errors caused by misspellings.

> **Automatic Creation and Injection of Built-In Helper Classes**. If Crux encounters an `[Inject]` tag for a property typed to `ServiceHelper`, `IServiceHelper`, `URLRequestHelper`, `IURLRequestHelper`, or `MockDelegateHelper`, and there is no matching `Bean` defined in a `BeanProvider`, Crux will automatically create a bean of the correct type and inject it for you.

## Inject by name {#inject-by-name}

If you have more than one bean of a given type defined you can request that a bean with a specific name be injected. This bean name must match the `id` attribute of the bean's tag as defined in your `BeanProvider`.

```as3
[Inject( source="userService" )]
public var service:RemoteObject;
 
...
 
// will inject this from BeanProvider
<mx:RemoteObject id="userService" />
```

> **Quick Tip**. `source` is the default attribute of `[Inject]`, so the above tag could also be written as `[Inject("userService")`]

## Inject bean property {#inject-bean-property}

Crux can also inject public bean properties, rather than just the beans themselves using dot notation. In the following example `userModel` is the name of a bean, and we are injecting its `currentUser` property.

```as3
[Inject( source="userModel.currentUser" )]
public var currentUser : User;
```

If the bean property is bindable and the decorated property is public, you can have Crux create a binding to the source property by adding `bind="true"` to the `[Inject]` tag:

```as3
[Inject( source="userModel.currentUser", bind="true" )]
public var currentUser : User;
```

you can also inject nested properties, such as:

```as3
[Inject( source="userModel.currentUser.firstName" )]
public var firstName : String;
```

## Two way bindings {#two-way-bindings}

To set up a reverse binding, so the bean property will receive updates made to the injection target, you can set the `twoWay` attribute of the `[Inject]` tag to true. This of course requires that the injection target is bindable as well.

```as3
[Bindable]
[Inject( source="userModel.currentUser", twoWay="true" )]
public var currentUser:User;
```

## Setter injection {#setter-injection}

Crux can also inject values into single argument methods. All of the attributes and policies mentioned above apply to setter injection as well, with the exception of `twoWay`.

```as3
[Inject]
public function setModel( model:UserModel ):void
{
    this.model = model;
}
```

## Injection destination {#injection-destination}

Sometimes it's useful to define an injection someplace other than directly on a property/method. This is especially true in **MXML** views, where decorating a child component's property is not possible. Rather than creating a local variable and binding your component property to it, you can simply use the destination attribute of `[Inject]`. If this were defined in an **MXML** file, it would be wrapped in a `Metadata` tag.

```as3
[Inject( source="userModel.currentMode", destination="modeViewStack.selectedIndex" )]
```

Take care to ensure that the injection destination will be created and available by the time your injections are processed. <!--The injection processing trigger can be configured in `CruxConfig`, but defaults to the ADDED_TO_STAGE event.-->
