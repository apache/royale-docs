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
description: The Jewel Button is a commonly used rectangular button with text inside. It looks like it can be pressed and allow users to take actions, and make choices, with a single click or tap.

---

# Jewel Button


## Reference

Available since version __0.9.4__

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.Button](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Button){:target='_blank'} | [org.apache.royale.jewel.supportClasses.button.BasicButton](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.button/BasicButton){:target='_blank'} |

<sup>_Note: This component is currently only available in JS_</sup>

## Overview

The Jewel `Button` component is a commonly used rectangular button with `text` or `html` inside. It looks like it can be pressed and allow users to take actions, and make choices, with a single click or tap.

Jewel Button can show different looks and feels. By default it appears light or dark finishes depending on the [jewel theme configuration](component-sets/jewel/jewel-theme-creation.html#theme-sass-file). Also using the `emphasis` property can be tinted with __PRIMARY__, __SECONDARY__ or __EMPHASIZED__ colors. These colors are as well defined in the jewel theme used.

It typically use event listeners to perform an action when the user interact with the control. When a user clicks the mouse or tap with the finger this control it dispatches a click event.

> If you doesn't need a text or label in your Button check BasicButton, located in the jewel supportClasses package since is more lightweight and fits that use case saving some bytes.

## Example of use

In MXML we can declare a button with a default look like this:

```mxml
<j:Button text="Button"/>
```

In ActionScript we can do the same in the following way: 

```as3
var b:Button = new Button();
b.text = "Button";
```

An example of `Button` can be seen as when click the following button:

<!--<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="300" 
src="assets/BE0002_Using_Jewel_Alert_Control/index.html"></iframe>-->

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.Button](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Button){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	    | Type   	| Description                                                                   |
|--------------	|----------	| -----------------------------------------------------------------------------	|
| __text__    	| _String_ 	| The text to appear on the control.                                            |
| __html__  	| _String_ 	| The html text to appear on the control.                                       |
| __emphasis__  | _String_  | Applies emphasis color display. Possible constant values are: PRIMARY, SECONDARY, EMPHASIZED. Colors are defined in royale jewel theme CSS. Left without value to get the default look (light or dark). 	|

### Methods

None.

## Relevant Events

`Button` component has many events like `rollOver`, `rollOut`, `mouseDown`, `mouseUp`, `mouseMove`, `mouseOut`, `mouseOver`, `mouseWheel` and `mouseWheel`, all of wich are of `org.apache.royale.events.MouseEvent` type, but the most important is the `click` event to trigger some action coded in the callback function.

You can attach callback listeners to the `click` as follows:

```mxml
<j:Button text="Button" click="clickHandler(event)"/>
```

the click event will use a clickHandler function written in ActionScript like this:

```mxml
<fx:Script>
    <![CDATA[      
        private function clickHandler(event:MouseEvent):void {
            trace("Hello from a Button!");
        }
    ]]>
</fx:Script>
```

When the user clicks the button the message _"Hello from a Button!"_ will be printed in the console log.

In ActionScript we can create a similar button in the following way: 

```as3
var b:Button = new Button();
b.text = "Button";
b.addEventListener('click', clickHandler);
```

## Relevant Beads

Unlike other components in Royale, Jewel `Button` does not has beads for _View_, _Controller_ or _Model_ in the Javascript platform.

In the other hand it can be used with other common control beads that provides more functionality. This beads are shared with many other Jewel controls.

### Common Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [Disabled](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'}      	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | This bead used to disable a jewel control.	|
| [MultiLine](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/MultiLine){:target='_blank'}       	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | The bead used with any [IClassSelectorListSupport](https://royale.apache.org/asdoc/index.html#!org.apache.royale.utils/IClassSelectorListSupport){:target='_blank'} control to allow more than one line. 	|
| [SizeControl](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/SizeControl){:target='_blank'} 	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | The bead used to to size a jewel control.           	|
| [ToolTip](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/ToolTip){:target='_blank'}     	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | The bead used to float a string over a control when the user hovers over it with a mouse |
| [Badge](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Badge){:target='_blank'}     	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | The bead used to provides a small status descriptors for a control       |

## Related controls

Other kind of jewel buttons you can be interested:

* [IconButton](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/IconButton){:target='_blank'}
* [ToggleButton](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/ToggleButton){:target='_blank'}