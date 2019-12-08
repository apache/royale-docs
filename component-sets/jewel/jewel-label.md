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
title: Jewel Label
description: The Jewel Label
permalink: /component-sets/jewel/label
---

# Jewel Label


## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.Label](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Label){:target='_blank'} | [org.apache.royale.core.supportClasses.StyledImageBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core.supportClasses/StyledImageBase){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel Label implements the Jewel control for single and multi line text labels. It dispatches a click event when the user clicks over it.

## Example of use

In __MXML__ declare a `Label` like this:

```mxml
<j:Label/>
```

In __ActionScript__ we can do the same in the following way: 

```as3
var label:Label = new Label();
parent.addElement(label);
```

where `parent` is the container where the control will be added.

Here is an example of the default label:

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="300" 
src="assets/jewel/jewel_label/index.html"></iframe>

[code here](https://github.com/apache/royale-docs/blob/master/assets/jewel/jewel_label/jewel_label.mxml){:target='_blank'}

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.Label](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Label){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	    | Type   	| Description                                                                   |
|--------------	|----------	| -----------------------------------------------------------------------------	|
| __text__    	| _String_ 	| The text inside the label.                                                    |
| __html__  	| _String_ 	| The html text inside the label.                                               |
| __multiline__ | _Boolean_ | false for single line. true for multiline.                                    |

### Methods

None.

## Relevant Events

The `Label` has _click_ event of type [org.apache.royale.events.Event](https://royale.apache.org/asdoc/index.html#!org.apache.royale.events/Event){:target='_blank'}. This event is dispatched when the user clicks the control and triggers some action coded in a callback function. Programatic changes will not trigger this event.

You can attach callback listeners to the _click_ event in __MXML__ as follows:

```mxml
<j:Label click="clickHandler(event)"/>
```

the _click_ event will use the `clickHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[      
        private function clickHandler(event:Event):void {
            trace("you clicked the label!");
        }
    ]]>
</fx:Script>
```

When the user clicks the label, the message _"you clicked the label!"_ will appear in the console log.

In __ActionScript__ we can add an event handler this way: 

```as3
var label:Label = new Label();
label.addEventListener('click', clickHandler);
parent.addElement(label);
```

## Relevant Beads

Unlike other components in Royale, the Jewel `Label` does not have beads for _View_ pr _Controller_ in the JavaScript platform, but has _Model_.

| Bead Type       	| Implementation                                            	| Description                                    	|
|-----------------	|-----------------------------------------------------------	|------------------------------------------------	|
| [IBeadModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadModel){:target='_blank'}      	| [org.apache.royale.jewel.beads.models.TextModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.models/TextModel){:target='_blank'}           	| The data model for the Label.                   	|

Jewel does not have beads specialy crafted for this control, but it can use other common Jewel control beads (shared with other controls) to provide more functionality.

### Label Beads

None

### Common Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [Disabled](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'}      	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | This bead lets you disable and enable a Jewel control.	|
| [SizeControl](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/SizeControl){:target='_blank'} 	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to give the Jewel control a custom size.           	|
| [ToolTip](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/ToolTip){:target='_blank'}     	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to enable floating a text string over the control when the user hovers the mouse cursor over it. |

## More examples

* [Binding the text property of a Jewel Label to update a text Label](https://royale.apache.org/binding-the-text-property-of-a-jewel-textinput-to-update-a-text-label/){:target='_blank'}
