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
title: Metadata
description: Decorate classes, properties and methods with extra information that can be used at compile or run time
permalink: /features/as3/metadata
---

# Metadata

Decorate classes, properties and methods with extra information that can be used at compile or run time

Metadata decorate classes, properties and methods to give extra data to the compiler that can be used to generate code at compile time that depends on that metadata values, or can be used at runtime for code that can interpret that data to perform some specific functionality. With [Apache Royale](https://royale.apache.org/), you can use meta in both [AS3](features/as3) and [MXML](features/mxml).

An example in **AS3** of a `Bindable` Metadata declaration decorating a variable is the following:

```as3
[Bindable]
public var someVariable:Boolean = true;
```

In **MXML* an example of an `Event` Metadata declared for that MXML file will be the following. Notice that you need to add to the special `fx:Metadata` tag:

```mxml
<fx:Metadata>
	[Event(name="someEvent", type="org.apache.royale.events.Event")]
</fx:Metadata>
```

## Available Metadata

Here you can find the list of all possible Royale Metadata available:

### Bindable

Bindable

### Event

Event

### DefaultProperty {#default-property}

The default property used when additional MXML content appears within an element's definition in an MXML file.

For example, [Jewel Group](component-sets/jewel/group) defines `[DefaultProperty("mxmlContent")]` in its class code. When using this component, instead of writting:

```mxml
<j:Group>
    <j:mxmlContent>
        <j:Button/>
    </j:mxmlContent>
</j:Group>
```

we can simplify declarations by removing `mxmlContent` tags saving several lines of code:

```mxml
<j:Group>
    <j:Button/>
</j:Group>
```

### RemoteObject

RemoteObject

### Managed

Managed

### ChangeEvent

ChangeEvent

### NonCommittingChangeEvent

NonCommittingChangeEvent

### Transient

Transient

### SWFOverride

SWFOverride

### Inspectable

Inspectable

### PercentProxy

PercentProxy

## Example of use

For example, you may create an **MXML** component that defines a new event. To make that event known to the Royale compiler that you can reference it in MXML, you insert the `[Event]` metadata tag into your component, as the following example shows:

```mxml
<fx:Metadata>
	[Event(name="someEvent")]
</fx:Metadata>
```

In this example, you use metadata to make the `someEvent` event available to the MXML compiler.

In an MXML file, you insert the metadata tags either in an <fx:Script> block along with your ActionScript code, or in an <fx:Metadata> block, as the following example shows:

```mxml
<j:Group xmlns:fx="http://ns.adobe.com/mxml/2009"
	xmlns:j="library://ns.apache.org/royale/jewel">

    <fx:Metadata>
        [Event("enableChange")]
    </fx:Metadata>

    <fx:Script>
    <![CDATA[
        private var _enable:Boolean;

        // Add the [Inspectable] metadata tag before the individual property.
        [Inspectable(defaultValue="false")]
        public function set enable(val:Boolean):void {
            _enable = val;
            this.enabled = val;

            // Define event object, initialize it, then dispatch it. 
            var eventObj:Event = new Event("enableChange");
            dispatchEvent(eventObj);
        }
    ]]>
    </fx:Script>
</j:Group>
```

When using metadata tags in ActionScript class files, you insert the metadata tag directly into the class definition; you do not use the <fx:Metadata> tag.
In AS3 you can use metadata as well in methods and properties of the class.

## Custom Metadata

You can create your own custom metadata. This info will come soon...
