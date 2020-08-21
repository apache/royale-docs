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
title: Jewel Container
description: The Jewel Container
permalink: /component-sets/jewel/container
---
[< Jewel Components list](component-sets/jewel)

# Jewel Container


## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           | Implements	                    |
|------------------------------	|----------------------------------	|---------------------------------  |
| [org.apache.royale.jewel.Container](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Container){:target='_blank'} | [Jewel ContainerBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.container/ContainerBase){:target='_blank'} | [org.apache.royale.core.IMXMLDocument](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IMXMLDocument){:target='_blank'} 	|

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel Container class is a container that adds up to the features already provided by [Jewel Group](component-sets/jewel/group).

The position and size of the children are determined by `BasicLayout` while the size of a Container can either be determined by its children or by specifying an exact size in pixels or as a percentage of the parent element. You can swap the layout for any other one available making children arrange in different ways (i.e: horizontal, vertical,...)

Container clip content by default thanks to its `Viewport` bead. This bead can also manage clipping trough `clipContent` property. To add scrolling functionality Viewport bead can be changed by `ScrollingViewport`.

Other Container feature are [View States](/features/view-states) to provide state management to show diferent parts of the interface to the user.

Finally Container can add elements directly to the strand (throught `strandChildren` property) instead to its view content unlike the `addElement()` APIs which place children into the `contentView`.

While the container is relatively lightweight, it should generally not be used as the base class for other controls, even if those controls are composed of children.  That's because the fundamental API of Container is to support an arbitrary set of children, and most controls only support a specific set of children.

## Example of use

In __MXML__ declare a `Container` like this:

```mxml
<j:Container width="200" height="200" className="wrapper">
    <j:Button text="Origin"/>
    <j:Button text="x:30,y:30" x="30" y="30"/>
    <j:Button text="x:60,y:60" x="60" y="60"/>
    <j:Button text="bottom/right" style="bottom:0;right:0"/>
</j:Container>
```

In __ActionScript__ we can do the same in the following way: 

```as3
var container:Container = new Container();
// add a button to the Container
var button:Button = new Button();
container.addElement(button);
// add the Container to the parent
parent.addElement(container);
```

where `parent` is the container where the control will be added.

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.Container](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Container){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	         | Type   	    | Description                                                                                           |
|------------------- |--------------| ------------------------------------------------------------------------------------------------------|
| __currentState__   | _String_ 	| The name of the current state.                                                                        |
| __numElements__    | _int_ 	    | The number of element children that can be laid out.                                                  |
| __mxmlContent__    | _Array_ 	    | The array of childs for this container. Is the [DefaultProperty](features/as3/metadata#default-property). |
| __states__         | _Array_ 	    | The array of view states. These should be instances of [org.apache.royale.states.State](https://royale.apache.org/asdoc/index.html#!org.apache.royale.states/State){:target='_blank'}|
| __strandChildren__ | _[IParent](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IParent){:target='_blank'}_ 	| An object to access the immediate children of the strand. |

### Methods

| Method    	       | Parameters                                                     |Description                                            |
|----------------------|----------------------------------------------------------------|-------------------------------------------------------|
| __addElement__   	   | c(IChild), dispatchEvent(Boolean=true) 	                    | Add a component to the parent.	                    |
| __addElementAt__     | c(IChild), index(int), dispatchEvent(Boolean=true) 	        | Add a component to the parent at the specified index.	|
| __getElementIndex__  | c(IChild)                                           	        | Gets the index of this subcomponent.	                |
| __getElementAt__     | index(int)                                         	        | Get a component from the parent at specified index.	|
| __removeElement__    | c(IChild), dispatchEvent(Boolean=true) 	                    | Remove a component from the parent.	                |

## Relevant Events

The most important event is `initComplete`, which indicates that the initialization of the container is complete.

Is needed when some action coded in a callback function need to be triggered as the container is ready to use after initialization.

You can attach callback listeners to the _initComplete_ event in __MXML__ as follows:

```mxml
<j:Container initComplete="initCompleteHandler(event)"/>
```

the _initComplete_ event will use the `initCompleteHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[      
        private function initCompleteHandler(event:Event):void {
            trace("Container is ready!");
        }
    ]]>
</fx:Script>
```

When the container is initialized the message _"Container is ready!"_ appears in the console log.

In __ActionScript__ we can add an event handler this way: 

```as3
var c:Container = new Container();
c.addEventListener('initComplete', initCompleteHandler);
parent.addElement(c);
```

## Relevant Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [ContainerView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads/ContainerView){:target='_blank'}      	| [org.apache.royale.core.IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'} | This is the default view bead.	|
| [BasicLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.layouts/BasicLayout){:target='_blank'}      	| [org.apache.royale.core.IBeadLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadLayout){:target='_blank'} | This is the default layout bead.	|

### Common Beads

Jewel `Container` can use any of the layout beads available in Jewel library. Also you can check [Related controls](component-sets/jewel/container.html#related-controls) section to see some preconfigured containers with specific layouts.

## More examples

* [Using Jewel TileHorizontalLayout](https://royale.codeoscopic.com/using-jewel-tilehorizontallayout/){:target='_blank'}
* [Using View States to show or hide content](https://royale.codeoscopic.com/using-view-states-to-show-or-hide-content/){:target='_blank'}
* [Customization through the Royale API](https://royale.codeoscopic.com/customization-through-the-royale-api/){:target='_blank'}

## Related controls {#related-controls}

Other useful Jewel containers components are:

* [HContainer](component-sets/jewel/hcontainer)
* [VContainer](component-sets/jewel/vcontainer)
* [Group](component-sets/jewel/group)
* [HGroup](component-sets/jewel/hgroup)
* [VGroup](component-sets/jewel/vgroup)


