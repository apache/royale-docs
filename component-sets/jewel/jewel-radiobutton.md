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
title: Jewel RadioButton
description: The Jewel RadioButton control lets the user choose one of a set of options.
permalink: /component-sets/jewel/radiobutton
---
[< Jewel Components list](component-sets/jewel)

# Jewel RadioButton

## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.RadioButton](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/RadioButton){:target='_blank'} | [org.apache.royale.jewel.supportClasses.button.SelectableButtonBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.button/SelectableButtonBase){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel RadioButton control lets the user choose one of a set of options. For each option there is a selectable circle and text that describes the option. Radio buttons always appear in groups of two or more with the same `groupName` property. When you select one radio button, any other button you may have previously selected in the group becomes deselected.

## Example of use

In __MXML__ declare a `RadioButton` like this:

```mxml
<j:RadioButton/>
```

In __ActionScript__ we can do the same in the following way: 

```as3
var radioButton:RadioButton = new RadioButton();
parent.addElement(radioButton);
```

where `parent` is the container where the control will be added.

Here is an example for this control:

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="300" 
src="assets/jewel/jewel_radiobutton/index.html"></iframe>

[code here](https://github.com/apache/royale-docs/blob/master/assets/jewel/jewel_radiobutton/jewel_radiobutton.mxml){:target='_blank'}

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.RadioButton](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/RadioButton){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	    | Type   	| Description                                                                   |
|--------------	|----------	| -----------------------------------------------------------------------------	|
| __selected__  | _Boolean_ | `true` if the check mark is displayed, `false` otherwise. Only one RadioButton can be selected at a time in the same group. |
| __selectedValue__  | _Object_ | The currently selected value in the group.                     |
| __text__  	| _String_ 	| The string used as a label.                                                   |
| __value__     | _String_  | The associated value.                                                         |
| __groupName__     | _String_  | The name of the group to which this radio button belongs. |

### Methods

None.

## Relevant Events

The `RadioButton` has a _change_ event of type [org.apache.royale.events.Event](https://royale.apache.org/asdoc/index.html#!org.apache.royale.events/Event){:target='_blank'}. This event is dispatched when the control is selected or deselected by the user. Notice that programmatic changes will not trigger this event.

Since this component is in essence a button, it has _click_ event as well. When the user clicks the radio button, it dispatches a normal _click_ event.

You can attach callback listeners to the _change_ event in MXML as follows:

```mxml
<j:RadioButton text="A RadioButton" value="somevalue" change="changeHandler(event)"/>
```

the _change_ event will use the `changeHandler` callback function you provide in ActionScript:

```mxml
<fx:Script>
    <![CDATA[
        private function changeHandler(event:Event):void {
            trace('RadioButton value is: ' + event.target.value, ' and selected state is: ' + event.target.selected);
        }
    ]]>
</fx:Script>
```

When the user clicks or presses the a radio button a message will be logged in the console showing the `value` and `selected` property values.

In ActionScript we can add an event handler this way: 

```as3
var radioButton:RadioButton = new RadioButton();
radioButton.text = "A RadioButton";
radioButton.value = "somevalue";
radioButton.addEventListener('change', changeHandler);
parent.addElement(radioButton);
```

## Relevant Beads

Unlike other components in Royale, the Jewel `RadioButton` does not have beads for _View_, _Controller_ or _Model_ in the JavaScript platform.

On the other hand, you can add other common Jewel control beads to it to provide more functionality. Many Jewel controls share these beads.

### Common Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [Disabled](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'}      	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | This bead lets you disable and enable a Jewel control.	|

## More examples

* [Creating a group of Jewel radio buttons](https://royale.apache.org/creating-a-group-of-jewel-radiobuttons/){:target='_blank'}

## Related controls

Other related Jewel components are:

* [CheckBox](component-sets/jewel/checkbox)
