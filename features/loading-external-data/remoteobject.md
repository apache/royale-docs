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
description: RemoteObject
permalink: /features/loading-external-data/remoteobject
---

# RemoteObject

Remote Procedure Calls with AMF Binary protocol

RemoteObject allows Apache Royale applications to make [Remote Procedure Calls (RPCs)](https://en.wikipedia.org/wiki/Remote_procedure_call){:target='_blank'} to a back-end server using [ActionScript Message Format (AMF) protocol](features/loading-external-data/amf). The server could be written in Java, PHP, ColdFusion, .NET, Ruby, Python or many other back-end technologies.

## Implementations

In Apache Royale we have two RemoteObject implementations:

* **MXRoyale**: Is the emulation of the Flex implementation. Is the best option if you're migrating from Flex since it support the same API Flex Framework use.

* **Network**: Is a newer bead implementation. This one is still under development, so you can find some issues that must to be solve

> We recommend to use the `MXRoyale` instead of `Network` version since is more close to the Flex implementation and is already use in Apache Royale applications currently in production.

## Example of use

In Apache Royale you can write an `mx:RemoteObject` in the following way:

```mxml
<fx:Declarations>
        <mx:RemoteObject id="serviceResp" fault="onFault(event)"
            endpoint="http://localhost:8080/messagebroker/websocket-amf"
            destination="exampleService"/>
</fx:Declarations>
```

You can write the `Network` implementation in the following way:

```mxml
<js:beads>
    <js:RemoteObject id="service"
        endPoint = "http://localhost:8080/messagebroker/websocket-amf"
        destination = "exampleService"
        result="onResult(event)" fault="onFault(event)"/>
</js:beads>
```

Don't forget to add the ClassAliasBead to the Application level beads:

```mxml
<j:beads>
    <js:ClassAliasBead />
</j:beads>
```

## Using ArrayCollection or ArrayList

In Apache Royale we support more collections types to receive data from the server. By Default RemoteObject uses `ArrayCollection` (like it was in Flex). If you are using Jewel components that use by default the new `ArrayList` class you would want to make RemoteObject encode and decode collections at client side using `ArrayList` class. You can do that in the following way.

```as3
registerClassAlias('org.apache.royale.collections.ArrayList', ArrayList);
```

## Considerations

RemoteObject in Apache Royale is very near to the Flex implementation and is working in some production applications migrated from Flex:

- **About Small Messages**: Apache Flex BlazeDS use by default special extra serialization through small messages. Small Messages are supported in Apache Royale implementation so you can left it on by default:

```xml
    <channel-definition ...>
        <properties>
            <serialization>
                <enable-small-messages>true</enable-small-messages>
            </serialization>
```

- **AMF Types not implemented yet**: Vector and Dictionary in Apache Royale AMF implementation is still not supported.

## Example projects available in Apache Royale

In the `examples` folder you can find some client implementations using `MXRoyale` and `Network` implementations of RemoteObject. As well using Basic or Jewel components. We describe in this section how to use the `MXRoyale` client and the Java server availables in our repositories:

* **RemoteObjectAMFTest-MXRoyale**: Is the Apache Royale Client that uses RemoteObject (with MXRoyale implementation) to communicate with the backend server to send and receive data via AMF. Is located in `example/mxroyale` folder. [Direct Link to this project](https://github.com/apache/royale-asjs/tree/develop/examples/mxroyale/RemoteObjectAMFTest)

* **SampleAmfWebApp**: Is a Java WebApp that uses [Apache Flex BlazeDS](https://github.com/apache/flex-blazeds){:target='_blank'} to expose some data and objects through an AMF endpoint. Is located in `example/amf` folder. [Direct Link to this project](https://github.com/apache/royale-asjs/tree/develop/examples/amf/SampleAmfWebApp)

> We don't have at the moment any example back end written in other languages like .NET, PHP, or Python. Community can submit AMF example servers to the project in other server languages.

To run this example localy you can follow this steps. Note: At this time some parts of the example only can be build with **maven**, we'll be providing at same time ANT build, but this is not priority. If you're interested in ANT build you can submit a PR.

1. Build **RemoteObjectAMFTest** with maven using "mvn clean install" from its folder. This generates the Apache Royale client.

2. Build **SampleAmfWebApp** with maven using "mvn clean install" from its folder. This generates the Java Web App with AMF support and will overlay the RemoteObjectAMFTest client compiled in the previous step.

> Notice that you can build other RemoteObject example available in our examples folder and change the SampleAmfWebApp pom.xml to overlay that one.

3. Launch **SampleAmfWebApp** in the embedded Jetty web server with "java -jar target/SampleAmfWebApp-0.9.6-SNAPSHOT-exec.war". you should be in root SampleAmfWebApp folder. _Notice: that SNAPSHOT number is just an example and can be different_

4.- In a browser launch "http://localhost:8080" and you would see the following:

{:align="center"}
![Apache Royale communication with AMF and RemoteObject Example](assets/images/RemoteObjectExample_1.jpeg)

## CompressedRemoteObject

A new RemoteObject, called CompressedRemoteObject, that performs compression has been added to Apache Royale. RemoteObjectAMFTest client and SampleAmfWebApp application has been updated to show this new feature. This remote object compress the AMF data with the zlib algorithm to improve the transfer times even more.

{:align="center"}
![CompressedRemoteObject Example](assets/images/RemoteObjectExample_2.png)

## SimpleRemoteObject

For more simple AMF backends probably RemoteObject will be more than you need. For this reason you can use SimpleRemoteObject that doesn't care about "clientId", or other BlazeDS functionalities.
