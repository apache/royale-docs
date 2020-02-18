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
title: Service Layer
description: Learn about how to interact with the server when using Crux
permalink: /libraries/crux/service-layer
---

# Service Layer

Learn about how to interact with the server when using Crux

Interacting with remote services is a feature found in almost every RIA, SPA or Web Application created. Because of this, Crux has made it a priority to streamline and enhance this aspect of development. There are four primary classes you will interact with in the service layer of your Crux application.

## ServiceHelper

The `ServiceHelper` class is probably the most common class you will use in the service layer of your Crux application. `ServiceHelper` is a class that simplifies and improves your interactions with service classes that return an `AsyncToken`. This includes `RemoteObject`, `HTTPService` and `WebService`. These services will typically be defined as beans and injected into one of your own classes. ServiceHelper's `executeServiceCall()` method is a concise way to call a service, define handlers for the call and specify objects to be passed to your result handler.

The following example shows a simple service call as it looks when using `ServiceHelper`. In this example the `ServiceHelper` has been defined as a bean and injected, but you can instantiate your own instance if you prefer. Also notice that you are able to define an array of parameters that will be passed to the result handler when the service returns. This can be very useful for maintaining context between calls and simplifying your result handler code. The first parameter of `executeServiceCall()` is an `AsyncToken` so we simply perform the `RemoteObject` method call, which returns an `AsyncToken`, inline.

```as3
[Inject( "userService" )]
public var ro:RemoteObject;
 
[Inject]
public var sh:ServiceHelper;
 
public function fetchUserRoles( user:User ):void
{
    sh.executeServiceCall( ro.fetchUserRoles( user.id ), fetchUserRoles_result, fetchUserRoles_fault, [ user ] );
}
 
protected function fetchUserRoles_result( data:Object, user:User ):void
{
    user.roles = data.result;
}
 
protected function fetchUserRoles_fault( info:Object ):void
{
    // handle service fault
}
```

## URLRequestHelper

Remote calls that do not return an `AsyncToken` are generally implemented using the `URLRequest` and `URLLoader` classes. Crux therefore provides the `URLRequestHelper` class, whose `executeURLRequest()` method works much like `executeServiceCall()`. The slight differences can be seen below, but can be summed up in that you do not directly create a `URLLoader` instance or call `load()` because Crux handles those aspects for you, and there are extra (optional) handlers that can be defined.

```as3
[Inject]
public var urh:URLRequestHelper;
 
public function loadConfig( user:User ):void
{
    urh.executeURLRequest( new URLRequest( "config.xml" ), loadConfig_result, loadConfig_fault,
                                                           loadConfig_progress, loadConfig_httpStatus, [ user ] );
}
 
protected function loadConfig_result( event:Event, user:User ):void
{
    user.config = XML( URLLoader( event.target ).data );
}
 
protected function loadConfig_fault( event:Event ):void
{
    // will be called in response to an IOErrorEvent.IO_ERROR or SecurityErrorEvent.SECURITY_ERROR
}
 
protected function loadConfig_progress( event:Event ):void
{
    // will be called in response to ProgressEvent.PROGRESS
}
 
protected function loadConfig_httpStatus( event:Event ):void
{
    // will be called in response to HTTPStatusEvent.HTTP_STATUS
}
```
