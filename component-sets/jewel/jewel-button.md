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
title: Jewel Button
description: The Jewel Button is a commonly-used rectangular button with a text label. Users can click or tap it to take an action.
permalink: /component-sets/jewel/button
---

# Jewel Button


## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.Button](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Button){:target='_blank'} | [org.apache.royale.jewel.supportClasses.button.SimpleButton](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.button/SimpleButton){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel Button is a commonly-used rectangular button with a text label. Users can click or tap it to take an action or make a choice.

The Jewel Button can have different looks and feels. By default it appears with light or dark highlights depending on the [Jewel theme configuration](component-sets/jewel/theme-creation#theme-sass-file). You can use the `emphasis` property to tint the button with __PRIMARY__, __SECONDARY__ or __EMPHASIZED__ colors (defined in the Jewel theme).

When a user interacts with the button (mouse over, long-press, double-click...) the button calls an event listener that can perform an action. When a user clicks the mouse on the button or taps the button on a touch screen, the button dispatches a click event.

> If you don't need a custom label on your button consider using Jewel's [SimpleButton](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.button/SimpleButton){:target='_blank'}, located in the Jewel `supportClasses` package, since it is more lightweight and will save you some bytes if it fits your use case.

## Example of use

In __MXML__ declare a `Button` with a default look like this:

```mxml
<j:Button text="Button"/>
```

In __ActionScript__ we can do the same in the following way: 

```as3
var button:Button = new Button();
button.text = "Button";
parent.addElement(button);
```

where `parent` is the container where the control will be added.

Here is an example of the default button:

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="300" 
src="assets/jewel/jewel_button/index.html"></iframe>

[code here](https://github.com/apache/royale-docs/blob/master/assets/jewel/jewel_button/jewel_button.mxml){:target='_blank'}
            

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.Button](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Button){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	    | Type   	| Description                                                                   |
|--------------	|----------	| -----------------------------------------------------------------------------	|
| __text__    	| _String_ 	| The text that appears on the button.                                            |
| __html__  	| _String_ 	| The html text that appears on the button.                                       |
| __emphasis__  | _String_  | Applies an emphasis color. Possible constant values are: PRIMARY, SECONDARY, EMPHASIZED. Colors are defined in the Royale Jewel theme CSS. If you don't select a value for this field, you get the default look (light or dark). 	|

### Methods

None.

## Relevant Events

The `Button` component has many events like `rollOver`, `rollOut`, `mouseDown`, `mouseUp`, `mouseMove`, `mouseOut`, `mouseOver`, and `mouseWheel`, all of which are of the type [org.apache.royale.events.MouseEvent](https://royale.apache.org/asdoc/index.html#!org.apache.royale.events/MouseEvent){:target='_blank'}. The most important event is `click`, which usually triggers some action coded in a callback function.

You can attach callback listeners to the _click_ event in __MXML__ as follows:

```mxml
<j:Button text="Button" click="clickHandler(event)"/>
```

the _click_ event will use the `clickHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[      
        private function clickHandler(event:MouseEvent):void {
            trace("Hello from a Button!");
        }
    ]]>
</fx:Script>
```

When the user clicks the button, the message _"Hello from a Button!"_ appears in the console log.

In __ActionScript__ we can add an event handler this way: 

```as3
var b:Button = new Button();
b.text = "Button";
b.addEventListener('click', clickHandler);
parent.addElement(button);
```

## Relevant Beads

Unlike other components in Royale, the Jewel `Button` does not have beads for _View_, _Controller_ or _Model_ in the JavaScript platform.

On the other hand, you can add to it other common Jewel control beads to provide more functionality. Many Jewel controls share these beads.

### Common Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [Disabled](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'}      	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | This bead lets you disable and enable a Jewel control.	|
| [MultiLine](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/MultiLine){:target='_blank'}       	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | The bead can be used with any [IClassSelectorListSupport](https://royale.apache.org/asdoc/index.html#!org.apache.royale.utils/IClassSelectorListSupport){:target='_blank'} control to allow more than one line of text. 	|
| [SizeControl](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/SizeControl){:target='_blank'} 	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to give the Jewel control a custom size.           	|
| [ToolTip](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/ToolTip){:target='_blank'}     	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to enable floating a text string over the control when the user hovers the mouse cursor over it. |
| [Badge](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Badge){:target='_blank'}     	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to provide small status descriptors for the control       |

## More examples

* [Using the Jewel Slider Control](https://royale.apache.org/using-the-jewel-slider-control/){:target='_blank'}
* [Selecting options from a group of Jewel CheckBox controls](https://royale.apache.org/selecting-options-from-a-group-of-jewel-checkbox-controls/){:target='_blank'}
* [Dividing an Apache Royale application with modules](https://royale.apache.org/dividing-an-apache-royale-application-with-modules/){:target='_blank'}

## Related controls

Other useful Jewel button components are:

* [IconButton](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/IconButton){:target='_blank'}
* [ToggleButton](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/ToggleButton){:target='_blank'}
