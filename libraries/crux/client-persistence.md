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
title: Client Persistence
description: Learn about how to persist data in the client using Crux
permalink: /libraries/crux/client-persistence
---

# Client Persistence

Learn about how to persist data in the client using Crux

Crux provides a bean to help with client persistence: `AMFStorageBean`. This bean the `AMFStorage` clasx under the hood that uses [AMF](features/loading-external-data/amf) to encode/decode data in browser's local storage.

> Using AMF simplifies development since you don't need to code additional methods for encode and decode your objects from/to the browser local storage, also it provides strong typing. Using JSON instead, will need more work from your side, while AMF does the heavy duty for you under the hood.

<!-- In AIR projects, you can also use the EncryptedLocalStorageBean, which can be found in the Crux Desktop Extensions project on GitHub. (The EncryptedLocalStorageBean is kept in a separate project to avoid having a framework dependency on the AIR libraries.) -->

## AMFStorageBean

To use the `AMFStorageBean`, you simply declare it in a `BeanProvider`:

```mxml
<crux:BeanProvider
    xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:crux="library://ns.apache.org/royale/crux">
  
    <crux:AMFStorageBean id="amfStorageBean" name="todomvc" localPath="crux"/>
 
</crux:BeanProvider>
```

Inject the instance into your model and declare a bindable getter/setter:

```as3
[Inject]
public var so:IAMFStorageBean;
  
[Bindable]
public function get appIndex():int
{
    // the second parameter is the initial value
    return so.getInt("appIndex", 0);
}
  
public function set appIndex(index:int):void
{
    so.setInt("appIndex", index);
}
```