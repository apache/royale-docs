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
title: Jewel DataContainer
description: The Jewel DataContainer
permalink: /component-sets/jewel/datacontainer
---
[< Jewel Components list](component-sets/jewel)

# Jewel DataContainer


## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           | Implements	                    |
|------------------------------	|----------------------------------	|---------------------------------  |
| [org.apache.royale.jewel.DataContainer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/DataContainer){:target='_blank'} | [Jewel ContainerBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.container/DataContainerBase){:target='_blank'} | [Jewel IListWithPresentationModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.list/IListWithPresentationModel){:target='_blank'} 	|

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel DataContainer class is a component that displays multiple data items.

This component gets the data through its `dataProvider` property that receives an `ArrayList` of data objects. To represent each item the component use an [ItemRenderer](/features/item-renderers) class that can be configured and customized. The component generate dynamically as many instances of ItemRenderer as items in the data provider array and fill each instance with the appropiate data. By default it uses `StringItemRenderer` as the item renderer.

By default items are layout vertically using Jewel `VerticalLayout`. This component has a `Viewport` that clip generated items.

## Example of use

In __MXML__ declare a `DataContainer` like this:

```mxml
<j:DataContainer width="100%" height="250">
    <js:ArrayList localId="avengers" source="[Iron Man, Hulk, Thor, Captain America, Black Widow]"/>
</j:DataContainer>
```

> Notice that we can nest the ArrayList directly to the DataContainer tag because "dataProvider" is its [DefaultProperty](features/as3/metadata#default-property).

In __ActionScript__ we can do the same in the following way: 

```as3
var dc:DataContainer = new DataContainer();
dc.dataProvider = new ArrayList(["Iron Man", "Hulk", "Thor", "Captain America", "Black Widow", "Hawkeye"]);
// add the Container to the parent
parent.addElement(dc);
```

where `parent` is the container where the control will be added.

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.DataContainer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/DataContainer){:target='_blank'} for a more detailed list of properties and methods.

