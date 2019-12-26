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

# Local Shared Object (LSO)

<!-- Based on material by Jeremy Mitchell at http://blog.flexdevelopers.com/2010/01/flex-basics-local-shared-object.html -->

Store user data in the equivalent of a cookie

Web browsers often store small amounts of data on a user's computer in a "cookie", a set of one or more name-value pairs in text. This information can be useful for session management and customizing the UI to match the user's needs and interests. Cookies have a bit of a bad name, though, because many applications and websites also use them for tracking user behavior and recording data the application really does not need in order to function.

Instead of using cookies, your Royale application can use Local Shared Objects (LSO) to store data on a user's computer. Local Shared Objects 

* can store up to 100 kb of data without asking the user's permission, much more than a cookie (4 kb).
* can store not only text values, but Number, String, Boolean, XML, Date, Array and Object name-value pairs.
* can even store instances of a custom class, if the class is registered using the _RemoteCass_ -metadata tag.
* have whatever name you give them, with the _.sol_ file type

> Storing data types and instances of a custom class use [AMF](features/loading-external-data/amf) encoding, which [RemoteObject](features/loading-external-data/remoteobject) also uses.

## Implementations

Apache Royalecurrently has two implementations of Local Shared Object:

- **SharedObject**: An emulation class to support the swf based Local Shared Object. This implementation supports AMF encoded content (requires `[RemoteClass]` or `registerClassAlias` before reading and writing to roundtrip instances of custom classes).

- **SharedObjectJSON**: A lighter-weight emulation class to make use of swf-based Local SharedObject support. This implementation does not support AMF encoded content. It is intended for JavaScript implementations that require persistence, but do not already have the AMF support dependency as part of the application.

Both classes can be found in the `MXRoyale` library.

## Create and retrieve a Local Shared Object

You use the same static method `getLocal()` to create a new Local Shared Object or to retrieve an existing one.

```as3
public static function getLocal(name:String, localPath:String = null, secure:Boolean = false):SharedObject
```

Then call the method and save the referrence in a variable:

```as3
var myNewLocalSharedObject:SharedObject = SharedObject.getLocal("myNewLocalSharedObject");
```

Royale looks for an existing `myNewLocalSharedObject.sol` file in the local directory on the user's computer. If it does not find one, Royale creates a new `.sol` file with that name. It then returns a reference to the file.

To see if the `.sol` file has any data (and, therefore, whether it is new), you can query its size:

```as3
var myNewLocalSharedObject:SharedObject = SharedObject.getLocal("myNewLocalSharedObject");
if (myNewLocalSharedObject.size > 0)
{
    trace("Existing Local Shared Object");
}
else
{
    trace("New Local Shared Object");
}
```

The `getLocal()` method has three parameters:

| Parameter     | Required  | Description                                                                   |
|--------------	|----------	| -----------------------------------------------------------------------------	|
| __name__    	| Yes       | Assigns a name to the Local Shared Object.                                    |
| __localPath__ | No        | You can use it if many components in the same application may be accessing the same Local Shared Object, rather than accessing the object your created in the app. |
| __secure__    | No        | If you create it, future calls to this Local Shared Object must use HTTPS.    |

## Access and update Local Shared Object values

A Local Shared Object can have many attributes. A Local Shared Object for each registered user of your app could include name, role, userID, age and other data your app needs to provide a good user experience. Each attribute is a property of the Local Shared Object's data property. You can read, update, or delete these values. For a Local Shared Object you have created for user __Alan Smithee__, __alansmithee.sol__, you can:

### Read LSO data

Create an instance of the Local Shared Object and populate it with the contents of the Local Shared Object on the user's computer.

```as3
var so:SharedObject = SharedObject.getLocal("alansmithee.sol");
```

#### Get the value of a specific property

Once you have read the Local Shared Object, you can get the values of specific properties.

```as3
var name:String = so.data.name;
var age:int = so.data.age;
```

### Update property values

You can update any of the existing values:

```as3
so.data.name= "John Smith";
so.data.age = 23;
so.data.orderIds = [23456, 24444, 25432];
```

A custom class must be registered and marked serializable using the `[RemoteClass]` metadata tag:

```as3
package {

    [RemoteClass]
    public class Address
    {
        public function Address(street:String)
        {
            this._street = street;
        }

        private var _street:String;

        public function get street():String
        {
            return _street;
        }
    }
}
```

Then used like this:

```as3
var address:Address = new Address();
address.street = "125 Foo Lane";
so.data.address = address;
```

### Delete values
You can delete values of specific properties, rather than replacing them.

```as3
delete so.data.age;
delete so.data.orderIds;
```

## Save a Local Shared Object

Use the `flush()` method to immediately write a Local Shared Object to the user's computer.

```as3
public function flush(minDiskSpace:int = 0):String
```

The `minDiskSpace` parameter is optional. Add a value to request additional space over 100 kb on the user's computer. If the value is greater than 0, the user sees a dialog box requesting the additional space.

A call to `flush()` returns either `SharedObjectFlushStatus.PENDING` or `SharedObjectFlushStatus.FLUSHED`. If the Local Shared Object needs more space than it currently has on the user's computer, the method returns `PENDING` and presents a dialog box to ask the user to grant more space.

When the user chooses either "Allow" or "Deny", the response dispatches a _NetStatusEvent.NET_STATUS_ event. Register an event listener to handle this event:

```as3
so.addEventListener(NetStatusEvent.NET_STATUS, netStatusHandler);
```

You can write a "save" function like this:

```as3
private function writeSharedObject():void
{
    var so:SharedObject = SharedObject.getLocal("mySO");
    so.data.name = "Alan Smithee";
    try
    {
        // wrap in a try to handle a scenario where local storage has been disallowed
        so.flush(500000);
    }
    catch (e:Error)
    {
        trace("Local storage is disabled for this domain");
    }
}
```

## Delete a Local Shared Object

Use the `clear()` method (``` public function clear():void ```) to delete a Local Shared Object and erase its data. If the Local Shared Object's name is "loginInfo", we could clear and delete it like this:

```as3
var so:SharedObject = SharedObject.getLocal("loginInfo");
so.clear();
```
