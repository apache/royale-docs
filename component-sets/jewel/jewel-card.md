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
title: Jewel Card
description: The Jewel Card
permalink: /component-sets/jewel/card
---
[< Jewel Components list](component-sets/jewel)

# Jewel Card

## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.Card](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Card){:target='_blank'} | [org.apache.royale.jewel.VContainer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/VContainer){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel Card class is a [Container](component-sets/jewel/container) for content like text or images that support optional parts like title and actions (mostly buttons) zones.

Card is a vertical container with a default "panel" styling that adds up to the features already provided by `VContainer`.

It can be use alone or with other complementary components listed below:

| Component 	             | Description                                                                                           |
|--------------------------- | ------------------------------------------------------------------------------------------------------|
| __CardHeader__             | a container to hold drawer header content (i.e: a title, image icon logo, or header actions)       	 |
| __CardTitle__              | a title label to use in the Card or inside the drawer header with specific styling        		     |
| __CardPrimaryContent__     | a container to hold card main content       						                                     |
| __CardExpandedContent__    | a container for content that need to remove all paddings and gaps with the surrounding Card           |
| __CardActions__            | a footer container to hold actions like buttons, icons or navigation       						     |

## Example of use

In __MXML__ declare a `Card` like this:

### Simple Card

This is the most basic jewel card that can be declared. Elements are layout vertically and with a default gap predefined in Jewel Theme.

```mxml
<j:Card>
    <j:CardTitle text="Jewel Simple Card"/>

    <j:Label text="This is the content"/>

    <j:Button text="Action" emphasis="primary"/>
</j:Card>
```

### Card with optional components

For advanced card layouts the next example shows how to use optional Card components.

First, we add a `CardHeader` with two `BarSection` components to separate the header content. In the left section we add the `CardTitle`and in the right one we add an `IconButton` (that provides an action, in the example we describe the actions as "Assign new data").

Next, we have a `CardPrimaryContent` with the main content. In this case some text description and a `ComboBox` component. Those elements are layout vertically with some gap between them.

Finally a `CardActions` with two `BarSection` (similar to card header). In the left we have a `Label` and in the right a `NumericStepper`.

```mxml
<j:Card>
	<j:CardHeader>
		<j:BarSection>
			<j:CardTitle text="Object Collection" className="secondary-normal"/>
		</j:BarSection>
		<j:BarSection itemsHorizontalAlign="itemsRight">
			<j:IconButton unboxed="true" click="assignNewData(avengersComboBox)">
				<j:icon>
					<js:MaterialIcon text="{MaterialIconType.SETTINGS_BACKUP_RESTORE}" />
				</j:icon>
				<j:beads>
					<j:ToolTip toolTip="Assign new data"/>
				</j:beads>
			</j:IconButton>
		</j:BarSection>
	</j:CardHeader>
	<j:CardPrimaryContent>
		<j:Label multiline="true">
			<j:html><![CDATA[<p>This <b>ComboBox</b> is using an object collection as <i>dataProvider</i>. Use <i>labelField</i> to indicate the object property to use as label. A <b>ComboBoxTextPrompt</b> bead is used to show a prompt message.</p>]]></j:html>
		</j:Label>
		<j:ComboBox localId="avengersComboBox" labelField="label" dataProvider="{listModel.avengers}">
			<j:beads>
				<j:ComboBoxTextPrompt prompt="Avengers Team..."/>
			</j:beads>
		</j:ComboBox>
	</j:CardPrimaryContent>
	<j:CardActions itemsVerticalAlign="itemsCenter">
		<j:BarSection>
			<j:Label localId="avengersComboBoxResult" html="{describeItem(avengersComboBox.selectedItem)}"/>
		</j:BarSection>
		<j:BarSection gap="3" itemsHorizontalAlign="itemsRight">
			<j:Label text="Select Index: "/>
			<j:NumericStepper valueChange="avengersComboBox.selectedIndex = event.target.value" minimum="0" maximum="8"/>
		</j:BarSection>
	</j:CardActions>
</j:Card>
```

In __ActionScript__ we can do the same in the following way. In this case we declare just the Card and a Label inside the card to keep it simple, otherwise these will be too verbose: 

```as3
var card:Card = new Card();
// add a label to the Card
var label:Label = new Label();
label.text = "Some text";
card.addElement(label);
// add the Container to the parent
parent.addElement(card);
```

where `parent` is the container where the control will be added.

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.Card](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Card){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	                | Type   	 | Description                                                                                           |
|-------------------------- |------------| ------------------------------------------------------------------------------------------------------|
| __currentState__          | _String_ 	 | The name of the current state.                                                                        |
| __itemsExpand__           | _Boolean_  | Make items resize to the fill all container space.                                                    |
| __itemsHorizontalAlign__  | _String_ 	 | Distribute all items horizontally. Possible values are: itemsLeft, itemsCenter, itemsRight, itemsSpaceBetween, itemsSpaceAround   |
| __itemsVerticalAlign__  | _String_ 	 | Distribute all items vertically. Possible values are: itemsSameHeight, itemsCenter, itemsTop, itemsBottom |
| __gap__                   | _Number_ 	 | Assigns variable gap in steps predefined in Jewel CSS.                                                |
| __numElements__           | _int_   	 | The number of element children that can be laid out.                                                  |
| __mxmlContent__           | _Array_ 	 | The array of childs for this group. Is the [DefaultProperty](features/as3/metadata#default-property). |
| __states__                | _Array_ 	 | The array of view states. These should be instances of [org.apache.royale.states.State](https://royale.apache.org/asdoc/index.html#!org.apache.royale.states/State){:target='_blank'}|
| __strandChildren__        | _[IParent](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IParent){:target='_blank'}_ 	| An object to access the immediate children of the strand. |
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

The most important event is `initComplete`, which indicates that the initialization of the card is complete.

Is needed when some action coded in a callback function need to be triggered as the card is ready to use after initialization.

You can attach callback listeners to the _initComplete_ event in __MXML__ as follows:

```mxml
<j:Card initComplete="initCompleteHandler(event)"/>
```

the _initComplete_ event will use the `initCompleteHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[      
        private function initCompleteHandler(event:Event):void {
            trace("Card is ready!");
        }
    ]]>
</fx:Script>
```

When the container is initialized the message _"Card is ready!"_ appears in the console log.

In __ActionScript__ we can add an event handler this way: 

```as3
var c:Card = new Card();
c.addEventListener('initComplete', initCompleteHandler);
parent.addElement(c);
```

## Relevant Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [ContainerView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads/ContainerView){:target='_blank'}      	| [org.apache.royale.core.IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'} | This is the default view bead.	|
| [VerticalLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.layouts/VerticalLayout){:target='_blank'}      	| [org.apache.royale.core.IBeadLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadLayout){:target='_blank'} | This is the default layout bead.	|
| [Viewport](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses/Viewport){:target='_blank'}      	| [org.apache.royale.core.IViewport](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IViewport){:target='_blank'} | Define the area that display content.	|


### Common Beads

Jewel `Card` can use any of the layout beads available in Jewel library. Also you can check [Related controls](component-sets/jewel/card.html#related-controls) section to see some preconfigured containers with specific layouts.

## More examples

* [Using Jewel TileHorizontalLayout](https://royale.codeoscopic.com/using-jewel-tilehorizontallayout/){:target='_blank'}
* [Using View States to show or hide content](https://royale.codeoscopic.com/using-view-states-to-show-or-hide-content/){:target='_blank'}
* [Customization through the Royale API](https://royale.codeoscopic.com/customization-through-the-royale-api/){:target='_blank'}

## Related controls {#related-controls}

Other useful Jewel containers components are:

* [Container](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Container){:target='_blank'}
* [HContainer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/HContainer){:target='_blank'}
* [VContainer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/VContainer){:target='_blank'}
* [Group](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Group){:target='_blank'}
* [HGroup](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/HGroup){:target='_blank'}
* [VGroup](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/VGroup){:target='_blank'}





