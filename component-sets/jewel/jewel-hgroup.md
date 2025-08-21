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
title: Jewel HGroup
description: The Jewel HGroup
permalink: /component-sets/jewel/hgroup
---
[< Jewel Components list](component-sets/jewel)

# Jewel HGroup

## Reference

Available since version __0.9.7__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.HGroup](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/HGroup){:target='_blank'} | [org.apache.royale.jewel.supportClasses.group.AlignmentItemsGroupWithGap](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.group/AlignmentItemsGroupWithGap){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel HGroup class is a [Group](component-sets/jewel/group) that lays out elements horizontally and provides some properties to allow more flexibility like `gap` to define spacing between items, and `itemsHorizontalAlign` and `itemsVerticalAlign` to distribute elements in different ways along the horizontal or vertical axis.

## Example of use

In __MXML__ declare a `HGroup` like this:

```mxml
<j:HGroup width="100%" height="300" gap="3" itemsHorizontalAlign="itemsCenter">
    <j:Card width="100" height="50%">
        <j:Label text="horz center"/>
    </j:Card>
    <j:Card width="100" height="50%">
        <j:Label text="horz center"/>
    </j:Card>
</j:HGroup>
```

In __ActionScript__ we can do the same in the following way. 

```as3
var hg:HGroup = new HGroup();
// add a label to the HGroup
var label:Label = new Label();
label.text = "Some text";
hg.addElement(label);
// add the HGroup to the parent
parent.addElement(hg);
```

where `parent` is the container to which the HGroup will be added.

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.HGroup](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/HGroup){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	                | Type   	 | Description                                                                                           |
|-------------------------- |------------| ------------------------------------------------------------------------------------------------------|
| __currentState__          | _String_ 	 | The name of the current state.                                                                        |
| __itemsExpand__           | _Boolean_  | Make items resize to the fill all container space.                                                    |
| __itemsHorizontalAlign__  | _String_ 	 | Distribute all items horizontaly. Possible values are: itemsLeft, itemsCenter, itemsRight, itemsSpaceBetween, itemsSpaceAround   |
| __itemsVerticalAlign__  | _String_ 	 | Distribute all items verticaly. Possible values are: itemsSameHeight, itemsCenter, itemsTop, itemsBottom |
| __gap__                   | _Number_ 	 | Assigns variable gap in steps predefined in Jewel CSS.                                                |
| __numElements__           | _int_   	 | The number of element children that can be laid out.                                                  |
| __mxmlContent__           | _Array_ 	 | The array of childs for this group. Is the [DefaultProperty](features/as3/metadata#default-property). |
| __states__                | _Array_ 	 | The array of view states. These should be instances of [org.apache.royale.states.State](https://royale.apache.org/asdoc/index.html#!org.apache.royale.states/State){:target='_blank'}|
| __variableRowHeight__     | _Boolean_ 	 | Specifies whether layout elements are allocated their preferred height.                               |

### Methods

| Method    	       | Parameters                                                     |Description                                            |
|----------------------|----------------------------------------------------------------|-------------------------------------------------------|
| __addElement__   	   | c(IChild), dispatchEvent(Boolean=true) 	                    | Add a component to the parent.	                    |
| __addElementAt__     | c(IChild), index(int), dispatchEvent(Boolean=true) 	        | Add a component to the parent at the specified index.	|
| __getElementIndex__  | c(IChild)                                           	        | Gets the index of this subcomponent.	                |
| __getElementAt__     | index(int)                                         	        | Get a component from the parent at specified index.	|
| __removeElement__    | c(IChild), dispatchEvent(Boolean=true) 	                    | Remove a component from the parent.	                |

## Relevant Events

The most important event is `initComplete`, which indicates that initialization of the group is complete.

It is needed when some action coded in a callback function needs to be triggered when the group is ready to use after initialization.

You can attach callback listeners to the _initComplete_ event in __MXML__ as follows:

```mxml
<j:HGroup initComplete="initCompleteHandler(event)"/>
```

the _initComplete_ event uses the `initCompleteHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[      
        private function initCompleteHandler(event:Event):void {
            trace("HGroup is ready!");
        }
    ]]>
</fx:Script>
```

When the group is initialized the message _"HGroup is ready!"_ appears in the console log.

In __ActionScript__ we can add an event handler this way: 

```as3
var hg:HGroup = new HGroup();
hg.addEventListener('initComplete', initCompleteHandler);
parent.addElement(hg);
```

## Relevant Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [GroupView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads/GroupView){:target='_blank'}      	| [org.apache.royale.core.IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'} | This is the default view bead.	|
| [HorizontalLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.layouts/HorizontalLayout){:target='_blank'}      	| [org.apache.royale.core.IBeadLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadLayout){:target='_blank'} | This is the default layout bead.	|

## Optional Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [ContainerDataBinding](https://royale.apache.org/asdoc/index.html#!org.apache.royale.binding/ContainerDataBinding){:target='_blank'}      	| [org.apache.royale.binding.DataBindingBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.binding/DataBindingBase){:target='_blank'} | Provide binding capabilities to the group.	|

## More examples

* [Using Jewel TileHorizontalLayout](https://royale.codeoscopic.com/using-jewel-tilehorizontallayout/){:target='_blank'}
* [Using View States to show or hide content](https://royale.codeoscopic.com/using-view-states-to-show-or-hide-content/){:target='_blank'}
* [Customization through the Royale API](https://royale.codeoscopic.com/customization-through-the-royale-api/){:target='_blank'}

## Related controls {#related-controls}

Other useful Jewel containers components are:

* [Group](component-sets/jewel/group)
* [VGroup](component-sets/jewel/vgroup)
* [Container](component-sets/jewel/container)
* [HContainer](component-sets/jewel/hcontainer)
* [VContainer](component-sets/jewel/vcontainer)
* [Card](component-sets/jewel/card)
