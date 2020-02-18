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
title: Interfaces
description: Learn more about the available interfaces in Crux
permalink: /libraries/crux/interfaces
---

# Interfaces

Learn more about the available interfaces in Crux

Crux provides several interfaces to enable manual control over certain features, or as an alternative to using certain metadata tags.

## ISetUpValidator

Implementing this interface will instruct Crux to invoke the `allowSetUp()` method of the bean before the bean is set up. If this method returns `true`, set up will proceed. If it returns `false`, Crux will not set up the bean.

## ITearDownValidator

Implementing this interface will instruct Crux to invoke the `allowTearDown()` method of the bean before the bean is torn down. If this method returns `true`, tear down will proceed. If it returns `false`, Crux will not tear down the bean.

> `ISetUpValidator` and `ITearDownValidator` are primarily meant for use in **view components**, to allow specific views to opt out of set up or tear down. In these cases, the developer can manually control set up or tear down of the views.

## IInitializing

Implementing this interface will instruct Crux to invoke the `afterPropertiesSet()` method of the bean after the bean is set up.

## IDisposable

Implementing this interface will instruct Crux to invoke the `destroy()` method of the bean when the bean is destroyed

## IDispatcherAware

Implementing this interface will instruct Crux to inject an `IEventDispatcher` into the bean's dispatcher property when it is set up. 

> **Best Practice**. In order to minimize coupling to the Crux framework, using the [PostConstruct], [PreDestroy] and [Dispatcher] metadata tags should be favored over use of IInitializing, IDisposable and IDispatcherAware.

## IBeanFactoryAware

Implementing this interface will instruct Crux to inject the Crux `IBeanFactory` into the bean's `beanFactory` property when it is set up.

## ICruxAware

Implementing this interface will instruct Crux to inject itself into the bean's `crux` property when it is set up.