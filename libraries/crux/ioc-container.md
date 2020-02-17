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
title: IoC Container
description: Crux IoC Container
permalink: /libraries/crux/ioc-container
---

# Crux IoC Container

Inversion of Control in Crux

Page Contents:

* [The BeanProvider Class](libraries/crux/ioc-container#bean-provider)
* [Prototype Beans](libraries/crux/ioc-container#prototype-beans)
* [Externalizing Configuration Values](libraries/crux/ioc-container#externalizing-configuration-values)

## The BeanProvider Class {#bean-provider}

The IoC (Inversion of control) container of Crux is the BeanProvider class. In the BeanProvider you typically define non-view classes that you want registered with the framework and available as injec

```mxml
<?xml version="1.0" encoding="utf-8"?>
<crux:BeanProvider
    xmlns:crux="library://ns.apache.org/royale/crux"
    xmlns:model="com.example.model.*"
    xmlns:control="com.example.control.*">

    <model:ApplicationModel id="applicationModel"/>
    <control:UserController id="userController"/>

</crux:BeanProvider>
```

Most applications define at least one `Beans.mxml` in the root package and pass it to the Crux tag's `beanProviders` property in the application’s main _MXML_ file. For clarity and simplicity, it is recommended that you define your beans in a separate file, using BeanProvider as the root tag, as shown above. However, if for some reason you choose to define your beans inline in the Crux tag, you'll need to wrap your objects with the Bean tag to ensure they are processed correctly:

```mxml
<crux:Crux>
    <crux:beanProviders>
        <crux:BeanProvider>
            <crux:Bean name="applicationModel">
                <model:ApplicationModel/>
            </crux:Bean>
            <crux:Bean name="userController">
                <control:UserController/>
            </crux:Bean> 
        </crux:BeanProvider>
    </crux:beanProviders>

    <crux:config>
        <crux:SwizConfig
            eventPackages="com.foo.events, org.bar.events"
            viewPackages="com.foo.views, org.bar.events"/>
    </crux:config>
</crux:Crux>
```

## Prototype Beans {#prototype-beans}

Similar to Spring’s [prototype scope](http://static.springsource.org/spring/docs/2.0.x/reference/beans.html#beans-factory-scopes-prototype){:target='_blank'}, Crux provides a `Prototype` tag. `Prototype` enables a few different things:

- **Constructor injection** – you can pass up to 8 arguments to your bean’s constructor
- **Unique copy for each injection target** (like prototype scope behavior in Spring)
- **Deferred instantiation** – Prototype beans will not be created until they are needed for injection

```mxml
<crux:Prototype id="editViewPresoModel"
    type="{ EditViewPresentationModel }"
    constructorArguments="{ someOtherBean }" />
```

> If you want deferred instantiation and/or constructor injection but not a unique copy for each injection you can set Prototype’s `singleton` property to true.

> A Prototype bean created and injected into a view is not destroyed when the view is removed. Crux cannot know what else you may have done with the Prototype. If you wish to tear down a Prototype bean when a view is removed, implement a `[PreDestroy]` method and dispatch a `TEAR_DOWN_BEAN` event for the Prototype bean.

## Externalizing Configuration Values {#externalizing-configuration-values}

`Bean` property values can also be defined in external __XML__ files. The `CruxConfigValueLoader` Crux extension provides one way to handle this. For example, an __XML__ file with this structure:

```xml
<config>
    <value1>This is value 1.</value1>
    <value2>This is value 2.</value2>
</config>
````

Can be loaded and used in a BeanProvider by doing:

```mxml
<externalconfig:CruxConfigValueLoader id="configLoader" source="config.xml" />
<controller:MyController id="myController"
    value1="{configLoader.configData.config.value1}"
    value2="{configLoader.configData.config.value2}" />
```

The `CruxConfigValueLoader` can be injected just like any other bean:

```as3
[Inject]
public var configLoader : CruxConfigValueLoader;
```

Finally, you can create an event handler to execute after the external data is loaded (remember to add "org.apache.royale.crux.externalconfig.event" to your `eventPackages`):

```as3
[EventHandler( event = "ConfigLoaderEvent.CONFIG_LOAD_COMPLETE", properties = "configData" )]
public function onConfigLoadComplete( configData : Object ) : void
{
    // You can now reference the value with syntax such as:
    // configData.config.value1, configData.config.value2, etc.
}
```