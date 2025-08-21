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
title: HTTPService
description: Loading external data through REST services
permalink: /working-with-data/loading-external-data/httpservice
---

# HTTPService

Loading external data through REST services

You can load external data in [Apache Royale](https://royale.apache.org/) using the `HTTPService` class. Use `HTTPService` to make _POST_, _GET_, _PUT_ and _DELETE_ operations for requests on external data for [REST](https://en.wikipedia.org/wiki/Representational_state_transfer){:target='_blank'} services.

## Implementations

In Apache Royale we have two `HTTPService` implementations:

* **MXRoyale**: Is an emulation of the implementation that Flex applications use. It is the best option if you're migrating from Flex since it supports the same API that the Flex framework uses.

* **Network**: Is a newer [bead](features/strands-and-beads) implementation. This is still under development, so you may run into some issues that will need to be resolved.

## Examples

In Apache Royale you can write an `mx:RemoteObject` like this:

```mxml
<fx:Declarations>
        <mx:HTTPService id="srv" useProxy="false" resultFormat="text"
            result="resultHandler(event)" fault="faultHandler(event)"/>
</fx:Declarations>
```

You can write the `Network` implementation like this:

```mxml
<js:beads>
    <js:HTTPService id="service">
        <js:LazyCollection id="collection">
            <js:inputParser>
                <js:JSONInputParser />
            </js:inputParser>
            <js:itemConverter>
                <local:StockDataJSONItemConverter />
            </js:itemConverter> 
        </js:LazyCollection>
    </js:HTTPService>
</js:beads>
```

## Example

- See this tutorial on [Loading external data through HTTPService](https://royale.apache.org/loading-external-data-through-httpservice/){:target='_blank'} 
