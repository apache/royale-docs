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
title: Jewel List
description: The Jewel List
permalink: /component-sets/jewel/list
---
[< Jewel Components list](component-sets/jewel)

# Jewel List

Available since version __0.9.4__.

| Class                 	    | Extends                           | Implements	                    |
|------------------------------	|----------------------------------	|---------------------------------  |
| [org.apache.royale.jewel.List](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/List){:target='_blank'} | [org.apache.royale.jewel.DataContainer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/DataContainer){:target='_blank'} | [IVariableRowHeight](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.layouts/IVariableRowHeight){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The List class is a [DataContainer](component-sets/jewel/datacontainer) component that provides item selection and keyboard navigation through items (check DataContainer for more info about core List functionality). If you just need to show a list of items you can use a `DataContainer`; if you need interaction with items, use `List`.

List default item renderer is [ListItemRenderer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.itemRenderers/ListItemRenderer){:target='_blank'}. When there's a need of any advanced item, we recommend using layout to extend ListItemRenderer to create a custom renderer. List can also use factories and data mappers for renderers that suport selection.

This component supports scrolling by default and gives you control over rollover and row height for each cell in every column. You can also programatically scroll to any item by index.  

## Example of use

In __MXML__ declare a `List` like this:

```mxml
<j:List width="100%" height="250">
    <js:ArrayList localId="avengers" source="[Iron Man, Hulk, Thor, Captain America, Black Widow, Hawkeye]"/>
</j:List>
```

>We can nest the ArrayList directly into the DataContainer tag because "dataProvider" is its [DefaultProperty](features/as3/metadata#default-property).

In __ActionScript__ we can do the same in the following way: 

```as3
var list:List = new List();
list.dataProvider = new ArrayList(["Iron Man", "Hulk", "Thor", "Captain America", "Black Widow", "Hawkeye"]);
// add the List to the parent
parent.addElement(list);
```

where `parent` is the container where the control will be added.


## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.List](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/List){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	               | Type   	    | Description                                                                                           |
|------------------------- |--------------| ------------------------------------------------------------------------------------------------------|
| __currentState__         | _String_ 	| The name of the current state.                                                                        |
| __itemRenderer__         | _String_ 	| The class or factory used to display each item.                                                       |
| __labelField__           | _String_ 	| The name of field within the data used for display.                                                   |
| __dataProvider__         | _Object_ 	| The data being display by the List. Is the [DefaultProperty](features/as3/metadata#default-property). In Jewel an [ArrayList](https://royale.apache.org/asdoc/index.html#!org.apache.royale.collections/ArrayList){:target='_blank'}                                             |
| __numElements__          | _int_ 	    | The number of element children that can be laid out.                                                  |
| __rollOverIndex__        | _int_ 	    | The index of the item currently below the pointer.                                                    |
| __rowHeight__            | _Number_ 	| The default height of each cell in every column.                                                      |
| __selectedIndex__        | _int_ 	    | The index of the currently selected item.                                                             |
| __selectedItem__         | _Object_ 	| The item currently selected.                                                                          |
| __states__               | _Array_ 	| The array of view states. These should be instances of [org.apache.royale.states.State](https://royale.apache.org/asdoc/index.html#!org.apache.royale.states/State){:target='_blank'}|
| __strandChildren__       | _[IParent](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IParent){:target='_blank'}_ 	| An object to access the immediate children of the strand. |
| __variableRowHeight__    | _Boolean_ 	| If false, the actual height of each layout element is the value of rowHeight. The default is true.   |

### Methods

| Method    	       | Parameters                                                     |Description                                                             |
|----------------------|----------------------------------------------------------------|------------------------------------------------------------------------|
| __addElement__   	   | c(IChild), dispatchEvent(Boolean=true) 	                    | Add a component to the parent.	                                     |
| __addElementAt__     | c(IChild), index(int), dispatchEvent(Boolean=true) 	        | Add a component to the parent at the specified index.	                 |
| __getElementIndex__  | c(IChild)                                           	        | Gets the index of this subcomponent.	                                 |
| __getElementAt__     | index(int)                                         	        | Get a component from the parent at specified index.	                 |
| __removeElement__    | c(IChild), dispatchEvent(Boolean=true) 	                    | Remove a component from the parent.	                                 |
| __scrollToIndex__    | index(int)                              	                    | Ensures that the data provider item at the given index is visible.     |

## Relevant Events

The most important event is `change`, which is dispatched whenever the list's selected item changes.


You can attach callback listeners to the _change_ event in __MXML__ as follows:

```mxml
<j:List change="changeHandler(event)"/>
```

the _change_ event will use the `changeHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[      
        private function changeHandler(event:Event):void {
            trace("[Selection] index", event.target.selectedIndex, "item", event.target.selectedItem);
        }
    ]]>
</fx:Script>
```

When the user selects any item a change event is dispatched and a message appears in the console log showing the "index" and the "item" that correspond to the selection.

> When a programmatic _change_ event is needed you can use the `selectionChanged` event instead to listen for selection changes.

In __ActionScript__ we can add an event handler this way: 

```as3
var list:List = new List();
list.addEventListener(Event.CHANGE, changeHandler);
parent.addElement(list);
```

## Relevant Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [ArrayListSelectionModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.models/ArrayListSelectionModel){:target='_blank'}      	| [IBeadModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadModel){:target='_blank'} | This is the default model bead.	|
| [ListSingleSelectionMouseController](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controllers/ListSingleSelectionMouseController){:target='_blank'}      	| [IBeadController](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadController){:target='_blank'} | This is the default controller for input and output.	|
| [ListView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.views/ListView){:target='_blank'}      	| [IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'} | This is the default view bead.	|
| [VerticalLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.layouts/VerticalLayout){:target='_blank'}      	| [IBeadLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadLayout){:target='_blank'} | This is the default layout bead.	|
| [SelectionDataItemRendererFactoryForCollectionView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads/SelectionDataItemRendererFactoryForCollectionView){:target='_blank'}      	| [IDataProviderItemRendererMapper](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IDataProviderItemRendererMapper){:target='_blank'} | Map data to itemrenders.	|
| [SelectableItemRendererClassFactory](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/SelectableItemRendererClassFactory){:target='_blank'}      	| [IItemRendererClassFactory](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IItemRendererClassFactory){:target='_blank'} | The factory of itemrenders.	|
| [ListItemRenderer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.itemRenderers/ListItemRenderer){:target='_blank'}      	| [IItemRenderer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IItemRenderer){:target='_blank'} | The itemrenders class to instantiate.	|
| [ListItemRendererInitializer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.itemRenderers/ListItemRendererInitializer){:target='_blank'}      	| [IItemRendererInitializer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IItemRendererInitializer){:target='_blank'} | Configuration of itemrenders to instantiate.	|
| [ScrollingViewport](https://royale.apache.org/asdoc/index.html#!rg.apache.royale.jewel.supportClasses.scrollbar/ScrollingViewport){:target='_blank'}      	| [IViewport](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IViewport){:target='_blank'} | Define the area that display content.	|

## Optional Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [HorizontalListScroll](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.list/HorizontalListScroll){:target='_blank'}      	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Provide horizontal scroll to the list.	|
| [ListAlternateRowColor](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.list/ListAlternateRowColor){:target='_blank'}      	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Provide alternate background color of every row with two colors.	|

### Common Beads

Jewel `List` can use any of the layout beads available in Jewel library. Also you can check [Related controls](component-sets/jewel/list.html#related-controls) section to see some advanced or preconfigured data containers.

## More examples

* [Adding an item to a Jewel List](https://royale.codeoscopic.com/adding-an-item-to-a-jewel-list/){:target='_blank'}
* [Using an Item Renderer with a List](https://royale.codeoscopic.com/using-an-item-renderer-with-a-list/){:target='_blank'}
* [Using Jewel TileHorizontalLayout](https://royale.codeoscopic.com/using-jewel-tilehorizontallayout/){:target='_blank'}

## Related controls {#related-controls}

Other useful Jewel containers components are:

* [DataGrid](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/DataGrid){:target='_blank'}
* [DataContainer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/DataContainer){:target='_blank'}
* [DropDownList](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/DropDownList){:target='_blank'}
* [Table](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Table){:target='_blank'}


