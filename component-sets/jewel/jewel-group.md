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
title: Jewel Group
description: The Jewel Group
permalink: /component-sets/jewel/group
---
[< Jewel Components list](component-sets/jewel)

# Jewel Group


## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           | Implements	                    |
|------------------------------	|----------------------------------	|---------------------------------  |
| [org.apache.royale.jewel.Group](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Group){:target='_blank'} | [Jewel GroupBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.group/GroupBase){:target='_blank'} | [org.apache.royale.core.IMXMLDocument](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IMXMLDocument){:target='_blank'} 	|

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel Group class provides a light-weight container for visual elements. By default the Group does not have a layout, allowing its children to be sized and positioned allowing its children to be sized and positioned using absolute positioning. You can swap the layout for any other one available making children arrange in different ways (i.e: horizontal, vertical,...)

The Jewel Group class provides a light-weight container for visual elements. By default Group have a Basiclayout, allowing its children to be positioned using absolute values (Notice Basic version doesn't provide any layout at all). Group doesn't clip content so elements inside the group aren't hidden far beyond group boundaries. Group doesn't have any chrome or visuals just position inner childs. 

Also, no scrolling support is built in Group. For scrolling and clipping you can use Jewel Container

## Example of use

In __MXML__ declare a `Group` like this:

```mxml
<j:Group width="200" height="200" className="wrapper">
    <j:Button text="Origin"/>
    <j:Button text="x:30,y:30" x="30" y="30"/>
    <j:Button text="x:60,y:60" x="60" y="60"/>
    <j:Button text="bottom/right" style="bottom:0;right:0"/>
</j:Group>
```

In __ActionScript__ we can do the same in the following way: 

```as3
var group:Group = new Group();
// add a button to the group
var button:Button = new Button();
group.addElement(button);
// add the group to the parent
parent.addElement(group);
```

where `parent` is the container where the control will be added.

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.Group](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Group){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	    | Type   	| Description                                                                   |
|--------------	|----------	| -----------------------------------------------------------------------------	|
| __currentState__    | _String_ 	| The name of the current state. |
| __mxmlContent__    | _Array_ 	| The array of childs for this group. Is the `DefaultProperty`. |
| __states__    | _Array_ 	| The array of view states. These should be instances of [org.apache.royale.states.State](https://royale.apache.org/asdoc/index.html#!org.apache.royale.states/State){:target='_blank'}|

### Methods

| Method    	    | Parameters                                                    |Description                                                                                      	|
|------------------	|-------------------------------------------------------------- |---------------------------------------------------------------------------------------------------|
| __addElement__   	| c(IChild), dispatchEvent(Boolean=true) 	                    | Add a component to the parent.	                    |
| __addElementAt__  | c(IChild), index(int), dispatchEvent(Boolean=true) 	        | Add a component to the parent at the specified index.	|
| __removeElement__ | c(IChild), dispatchEvent(Boolean=true) 	                    | Remove a component from the parent.	                |

## Relevant Events

The most important event is `initComplete`, which indicates that the initialization of the group is complete.

Is needed when some action coded in a callback function need to be triggered as the group is ready to use after initialization.

You can attach callback listeners to the _initComplete_ event in __MXML__ as follows:

```mxml
<j:Group initComplete="initCompleteHandler(event)"/>
```

the _initComplete_ event will use the `initCompleteHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[      
        private function initCompleteHandler(event:Event):void {
            trace("Group is ready!");
        }
    ]]>
</fx:Script>
```

When the group is initialized the message _"Group is ready!"_ appears in the console log.

In __ActionScript__ we can add an event handler this way: 

```as3
var g:Group = new Group();
g.addEventListener('initComplete', initCompleteHandler);
parent.addElement(g);
```

## Relevant Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [GroupView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads/GroupView){:target='_blank'}      	| [org.apache.royale.core.IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'} | This is the default view bead.	|
| [BasicLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.layouts/BasicLayout){:target='_blank'}      	| [org.apache.royale.core.IBeadLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadLayout){:target='_blank'} | This is the default layout bead.	|

### Common Beads

Jewel `Group` can use any of the layout beads available in Jewel library. Also you can check [Related controls](#related-controls) section to see some preconfigured groups with specific layouts.


## More examples

* [Using Jewel TileHorizontalLayout](https://royale.codeoscopic.com/using-jewel-tilehorizontallayout/){:target='_blank'}
* [Using View States to show or hide content](https://royale.codeoscopic.com/using-view-states-to-show-or-hide-content/){:target='_blank'}
* [Customization through the Royale API](https://royale.codeoscopic.com/customization-through-the-royale-api/){:target='_blank'}

## Related controls {#related-controls}

Other useful Jewel group components are:

* [HGroup](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/HGroup){:target='_blank'}
* [VGroup](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/VGroup){:target='_blank'}
* [Container](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Container){:target='_blank'}