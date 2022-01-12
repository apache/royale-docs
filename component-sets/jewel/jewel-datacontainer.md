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

This component gets the data through its `dataProvider` property that receives an `ArrayList` of data objects. To represent each item the component uses a suitably-configured [ItemRenderer](working-with-data/item-renderers) class. The component generates dynamically as many instances of its ItemRenderer as there are items in the data provider array, and fills each instance with the appropiate data. By default it uses `StringItemRenderer` as the item renderer.

By default items are laid out vertically using Jewel `VerticalLayout`. This component has a `Viewport` that clips generated items.

## Example of use

In __MXML__ declare a `DataContainer` like this:

```mxml
<j:DataContainer width="100%" height="250">
    <js:ArrayList localId="avengers" source="[Iron Man, Hulk, Thor, Captain America, Black Widow, Hawkeye]"/>
</j:DataContainer>
```

> Note that we can nest the ArrayList directly to the DataContainer tag because "dataProvider" is its [DefaultProperty](features/as3/metadata#default-property).

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

### Properties

| PROPERTY 	         | Type   	    | Description                                                                                           |
|------------------- |--------------| ------------------------------------------------------------------------------------------------------|
| __currentState__   | _String_ 	| The name of the current state.                                                                        |
| __itemRenderer__   | _String_ 	| The class or factory used to display each item.                                                       |
| __labelField__     | _String_ 	| The name of field within the data used for display.                                                   |
| __dataProvider__   | _Object_ 	| The data being display by the List. Is the [DefaultProperty](features/as3/metadata#default-property). In Jewel an [ArrayList](https://royale.apache.org/asdoc/index.html#!org.apache.royale.collections/ArrayList){:target='_blank'}                                             |
| __numElements__    | _int_ 	    | The number of element children that can be laid out.                                                  |
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

The most important event is `initComplete`, which indicates that initialization of the container is complete.

It is needed when some action coded in a callback function needs to be triggered when the data container is ready to use after initialization.

You can attach callback listeners to the _initComplete_ event in __MXML__ as follows:

```mxml
<j:DataContainer initComplete="initCompleteHandler(event)"/>
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

When the data container is initialized the message _"Container is ready!"_ appears in the console log.

In __ActionScript__ we can add an event handler this way: 

```as3
var dc:DataContainer = new DataContainer();
dc.addEventListener('initComplete', initCompleteHandler);
parent.addElement(dc);
```

## Relevant Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [DataProviderModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.models/DataProviderModel){:target='_blank'}      	| [org.apache.royale.core.IBeadModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadModel){:target='_blank'} | This is the default model bead.	|
| [DataContainerView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads/DataContainerView){:target='_blank'}      	| [org.apache.royale.core.IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'} | This is the default view bead.	|
| [VerticalLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.layouts/VerticalLayout){:target='_blank'}      	| [org.apache.royale.core.IBeadLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadLayout){:target='_blank'} | This is the default layout bead.	|
| [DataItemRendererFactoryForCollectionView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads/DataItemRendererFactoryForCollectionView){:target='_blank'}      	| [IDataProviderItemRendererMapper](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IDataProviderItemRendererMapper){:target='_blank'} | Map data to itemrenders.	|
| [ItemRendererClassFactory](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/ItemRendererClassFactory){:target='_blank'}      	| [IItemRendererClassFactory](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IItemRendererClassFactory){:target='_blank'} | The factory of itemrenders.	|
| [StringItemRenderer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.itemRenderers/StringItemRenderer){:target='_blank'}      	| [org.apache.royale.core.IItemRenderer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IItemRenderer){:target='_blank'} | The itemrenders class to instantiate.	|
| [DataContainerItemRendererInitializer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.itemRenderers/DataContainerItemRendererInitializer){:target='_blank'}      	| [IItemRendererInitializer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IItemRendererInitializer){:target='_blank'} | Configuration of itemrenders to instantiate.	|
| [Viewport](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses/Viewport){:target='_blank'}      	| [org.apache.royale.core.IViewport](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IViewport){:target='_blank'} | Define the area that display content.	|

### Common Beads

Jewel `DataContainer` can use any of the layout beads available in the Jewel library. Also you can check the [Related controls](component-sets/jewel/datacontainer.html#related-controls) section to see some advanced or preconfigured data containers.

## More examples

* [Adding an item to a Jewel List](https://royale.codeoscopic.com/adding-an-item-to-a-jewel-list/){:target='_blank'}
* [Using an Item Renderer with a List](https://royale.codeoscopic.com/using-an-item-renderer-with-a-list/){:target='_blank'}
* [Using Jewel TileHorizontalLayout](https://royale.codeoscopic.com/using-jewel-tilehorizontallayout/){:target='_blank'}

## Related controls {#related-controls}

Other useful Jewel containers components are:

* [List](component-sets/jewel/list)
* [DropDownList](component-sets/jewel/dropdownlist)
* [Table](component-sets/jewel/table)


