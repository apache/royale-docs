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
| [org.apache.royale.jewel.Container](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Container){:target='_blank'} | [Jewel ContainerBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.group/ContainerBase){:target='_blank'} | [org.apache.royale.core.IMXMLDocument](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IMXMLDocument){:target='_blank'} 	|

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel Container class is a container that adds up to the features already provided by Jewel Group.

The position and size of the children are determined by BasicLayout while the size of a Container can either be determined by its children or by specifying an exact size in pixels or as a percentage of the parent element. You can swap the layout for any other one available making children arrange in different ways (i.e: horizontal, vertical,...)

Container clip content by default thanks to its Viewport bead. This bead can also manage clipping trough `clipContent` property. To add scrolling functionality Viewport bead can be changed by ScrollingViewport.

Other Group feature are "View States" to provide state management to show diferent parts to the user.

Finally Container can add elements directly to the strand (throught `strandChildren` property) instead to its view content unlike the `addElement()` APIs which place children into the contentView.

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
var Container:Container = new Container();
// add a button to the Container
var button:Button = new Button();
Container.addElement(button);
// add the Container to the parent
parent.addElement(Container);
```

where `parent` is the container where the control will be added.


