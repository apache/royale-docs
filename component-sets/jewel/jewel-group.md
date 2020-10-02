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

<sup>_Note: This component is currently only available for applications compiled into JavaScript._</sup>

## Overview

The Jewel Group class provides a lightweight container for visual elements. By default the group has a Basic Layout, so you can size and position its children with absolute positioning (the Basic layout groups the children, but does not provide layout information). You can swap the layout for any other one available (for instance horizontal or vertical) to arrange the children in different ways. The group doesn't clip content, so elements inside the group aren't hidden if they extend beyond the group boundaries. The group doesn't have any chrome or visuals; it just contains the children. 

Also, the group has no scrolling support. For scrolling and clipping you can use [Jewel Container](component-sets/jewel/container).

While the container is relatively lightweight, you should generally not use it as the base class for other controls, even if those controls are composed of children.  That's because the fundamental API of Container is to support an arbitrary set of children, and most controls only support a specific set of children.

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

| PROPERTY 	         | Type   	    | Description                                                                                           |
|------------------- |--------------| ------------------------------------------------------------------------------------------------------|
| __currentState__   | _String_ 	| The name of the current state.                                                                        |
| __numElements__    | _int_ 	    | The number of element children that can be laid out.                                                  |
| __mxmlContent__    | _Array_ 	    | The array of childs for this group. Is the [DefaultProperty](features/as3/metadata#default-property). |
| __states__         | _Array_ 	    | The array of view states. These should be instances of [org.apache.royale.states.State](https://royale.apache.org/asdoc/index.html#!org.apache.royale.states/State){:target='_blank'}|

### Methods

| Method    	       | Parameters                                                     |Description                                            |
|----------------------|----------------------------------------------------------------|-------------------------------------------------------|
| __addElement__   	   | c(IChild), dispatchEvent(Boolean=true) 	                    | Add a component to the parent.	                    |
| __addElementAt__     | c(IChild), index(int), dispatchEvent(Boolean=true) 	        | Add a component to the parent at the specified index.	|
| __getElementIndex__  | c(IChild)                                           	        | Gets the index of this subcomponent.	                |
| __getElementAt__     | index(int)                                         	        | Get a component from the parent at specified index.	|
| __removeElement__    | c(IChild), dispatchEvent(Boolean=true) 	                    | Remove a component from the parent.	                |

## Relevant Events

The most important event is `initComplete`, which indicates that initialization of the group is complete. You can use this when some action coded in a callback function need to be triggered when the group has initialized and is ready to use.

You can attach callback listeners to the _initComplete_ event in __MXML__ as follows:

```mxml
<j:Group initComplete="initCompleteHandler(event)"/>
```

the _initComplete_ event uses the `initCompleteHandler` callback function you provide in __ActionScript__:

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

## Optional Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [ContainerDataBinding](https://royale.apache.org/asdoc/index.html#!org.apache.royale.binding/ContainerDataBinding){:target='_blank'}      	| [org.apache.royale.binding.DataBindingBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.binding/DataBindingBase){:target='_blank'} | Provide binding capabilities to the group.	|

### Common Beads

Jewel `Group` can use any of the layout beads available in Jewel library. Also you can check [Related controls](component-sets/jewel/group.html#related-controls) section to see some preconfigured groups with specific layouts.

## More examples

* [Using Jewel TileHorizontalLayout](https://royale.codeoscopic.com/using-jewel-tilehorizontallayout/){:target='_blank'}
* [Using View States to show or hide content](https://royale.codeoscopic.com/using-view-states-to-show-or-hide-content/){:target='_blank'}
* [Customization through the Royale API](https://royale.codeoscopic.com/customization-through-the-royale-api/){:target='_blank'}

## Related controls {#related-controls}

Other useful Jewel group components are:

* [HGroup](component-sets/jewel/hgroup)
* [VGroup](component-sets/jewel/vgroup)
* [Container](component-sets/jewel/container)
* [HContainer](component-sets/jewel/hcontainer)
* [VContainer](component-sets/jewel/vcontainer)
