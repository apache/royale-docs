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
title: Local Shared Object
description: Use LocalSharedObject to store user or session data
permalink: /features/loading-external-data/localsharedobject
---

# Local Shared Object

Store user data in the equivalent of a cookie

Web browsers often store small amounts of data on a user's computer in a "cookie", a set of one or more name-value pairs in text. This information can be useful for session management and customizing the UI to match the user's needs and interests. Cookies have a bit of a bad name, though, because many applications and websites also use them for tracking user behavior and recording data the application really does not need in order to function.

Instead of using cookies, your Royale application can use Local Shared Objects to store data on a user's computer. Local Shared Objects 

* can store up to 100 kb of data without asking the user's permission, much more than a cookie (4 kb).
* can store not only text values, but Number, String, Boolean, XML, Date, Array and Object name-value pairs.
* can even store instances of a custom class, if the class is registered using the _RemoteCass_ -metadata tag.
* have whatever name you give them, with the _.sol_ file type

## Create and retrieve a Local Shared Object

_information coming soon_

## Access and update Local Shared Object values

_information coming soon_

## Save a Local Shared Object

_information coming soon_

## Delete a Local Shared Object

Use the _clear()_ method (``` public function clear():void ```) to delete a Local Shared Object and erase its data. If the Local Shared Object's name is "loginInfo", we could clear and delete it like this:

```
var so:SharedObject = SharedObject.getLocal("loginInfo");
so.clear();
```






