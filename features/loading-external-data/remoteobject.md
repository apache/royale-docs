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
title: RemoteObject
description: Remote procedure calls with the AMF binary protocol
permalink: /features/loading-external-data/remoteobject
---

# RemoteObject

Remote procedure calls with the AMF binary protocol

RemoteObject lets Apache Royale applications make [Remote Procedure Calls (RPCs)](https://en.wikipedia.org/wiki/Remote_procedure_call){:target='_blank'} to a back-end server using the [ActionScript Message Format (AMF) protocol](features/loading-external-data/amf). The server can be written in Java, PHP, ColdFusion, .NET, Ruby, Python or many other back-end technologies.

## Implementations

In Apache Royale we have two `RemoteObject` implementations:

* **MXRoyale**: Is an emulation of the implementation that Flex applications use. It is the best option if you're migrating from Flex since it supports the same API that the Flex framework uses.

* **Network**: Is a newer bead implementation. This is still under development, so you may run into some issues that will need to be resolved.

> We recommend using `MXRoyale` instead of the `Network` version for now, since it is closer to the Flex implementation and is already in use in Apache Royale applications currently in production.

## Examples

In Apache Royale you can write an `mx:RemoteObject` like this:

```mxml
<fx:Declarations>
        <mx:RemoteObject id="serviceResp" fault="onFault(event)"
            endpoint="http://localhost:8080/messagebroker/websocket-amf"
            destination="exampleService"/>
</fx:Declarations>
```

You can write the `Network` implementation like this:

```mxml
<js:beads>
    <js:RemoteObject id="service"
        endPoint = "http://localhost:8080/messagebroker/websocket-amf"
        destination = "exampleService"
        result="onResult(event)" fault="onFault(event)"/>
</js:beads>
```

Don't forget to add _ClassAliasBead_ to the Application level beads:

```mxml
<j:beads>
    <js:ClassAliasBead />
</j:beads>
```

## Using ArrayCollection or ArrayList

In Apache Royale we support several types of collections types to display external data your app. By default, as it was with Flex apps, RemoteObject uses `ArrayCollection`. If you are using Jewel components that use by default the new `ArrayList` class you would want to make RemoteObject encode and decode collections at the client side using `ArrayList`. You can do that in the following way.

```as3
registerClassAlias('org.apache.royale.collections.ArrayList', ArrayList);
```

## Notes

- **Small Messages**: Apache Flex BlazeDS uses by default an extra serialization through Small Messages. Royale supports Small Messages so you can leave that feature on:

```xml
    <channel-definition ...>
        <properties>
            <serialization>
                <enable-small-messages>true</enable-small-messages>
            </serialization>
```

- **AMF Types**: Royale's AMF implementation does not yet support Vector or Dictionary.

## Example projects

In the `examples` folder you can find some client implementations using `MXRoyale` and `Network` implementations of RemoteObject, with both Basic or Jewel components. We describe in this section how to use the `MXRoyale` client and the Java server availables in our repositories:

* **RemoteObjectAMFTest-MXRoyale**: Is the Apache Royale Client that uses RemoteObject (with MXRoyale implementation) to communicate with the backend server to send and receive data via AMF. It is located in the `example/mxroyale` folder. [Direct Link to this project](https://github.com/apache/royale-asjs/tree/develop/examples/mxroyale/RemoteObjectAMFTest)

* **SampleAmfWebApp**: Is a Java WebApp that uses [Apache Flex BlazeDS](https://github.com/apache/flex-blazeds){:target='_blank'} to expose some data and objects through an AMF endpoint. It is located in the `example/amf` folder. [Direct Link to this project](https://github.com/apache/royale-asjs/tree/develop/examples/amf/SampleAmfWebApp)

> We don't yet have example back end code written in other languages like .NET, PHP, or Python. You are welcome to submit AMF examples to the project in other server languages.

To run this example localy, follow these steps. 
> Note: At this time some parts of the example only can be built with **maven**, we'll be providing at some time an ANT build, but this is not a priority. If you're interested in an ANT build you can submit a PR.

1. Build **RemoteObjectAMFTest** with maven using "mvn clean install" from its folder. This generates the Apache Royale client.

2. Build **SampleAmfWebApp** with maven using "mvn clean install" from its folder. This generates the Java Web App with AMF support and will overlay the RemoteObjectAMFTest client compiled in the previous step.

>You can build other RemoteObject examples from our examples folder and change the SampleAmfWebApp pom.xml to overlay that one.

3. Launch **SampleAmfWebApp** in the embedded Jetty web server with "java -jar target/SampleAmfWebApp-0.9.6-SNAPSHOT-exec.war". You should be in the root SampleAmfWebApp folder. _Notice: that the SNAPSHOT number is just an example and can be different_

4.- In a browser launch "http://localhost:8080" and you would see the following:

{:align="center"}
![Apache Royale communication with AMF and RemoteObject Example](assets/images/RemoteObjectExample_1.jpeg)

## CompressedRemoteObject

A new RemoteObject that performs compression, CompressedRemoteObject, has been added to Apache Royale. RemoteObjectAMFTest client and SampleAmfWebApp application have been updated to show this new feature. This remote object compresses the AMF data with the zlib algorithm to improve transfer times.

{:align="center"}
![CompressedRemoteObject Example](assets/images/RemoteObjectExample_2.png)

## SimpleRemoteObject

For more simple AMF backends RemoteObject will be allt that you need. You can use SimpleRemoteObject that doesn't care about "clientId", or other BlazeDS functionality.
