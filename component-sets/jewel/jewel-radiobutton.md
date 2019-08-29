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
description: The Jewel RadioButton control lets the user make a single choice within a set of mutually exclusive choices.

---

# Jewel RadioButton

## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.RadioButton](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/RadioButton){:target='_blank'} | [org.apache.royale.jewel.supportClasses.button.SelectableButtonBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.button/SelectableButtonBase){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel RadioButton control lets the user make a single choice within a set of mutually exclusive choices. A RadioButton consists of a circle and, typically, text that clearly communicates a condition that will be set when the user clicks or touches it. Radio buttons always appear in groups of two or more with the same `groupName` property. While they can be individually selected, can only be deselected by selecting a different RadioButton in the same group (which deselects the rest of RadioButton).

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
| __selected__  | _Boolean_ | `true` if the check mark is displayed, `false` otherwise. Only one RadioButton can be selected in the same group. |
| __selectedValue__  | _Object_ | The currently selected value in the group.                     |
| __text__  	| _String_ 	| The string used as a label.                                                   |
| __value__     | _String_  | The associated value.                                                         |
| __groupName__     | _String_  | The name of the group to which this radio belongs. |

### Methods

None.

## Relevant Events

The `RadioButton` has _change_ event of type [org.apache.royale.events.Event](https://royale.apache.org/asdoc/index.html#!org.apache.royale.events/Event){:target='_blank'}. This event is dispatched when the control is selected or deselected by the user. Notice that programatic changes will not trigger this event.

Since this component is in essence a button, it has _click_ event as well, so when the control is clicked by the user it dispatches a normal _click_ event as usual.

You can attach callback listeners to the _change_ event in __MXML__ as follows:

```mxml
<j:RadioButton text="A RadioButton" value="somevalue" change="changeHandler(event)"/>
```

the _change_ event will use the `changeHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[
        private function changeHandler(event:Event):void {
            trace('RadioButton value is: ' + event.target.value, ' and selected state is: ' + event.target.selected);
        }
    ]]>
</fx:Script>
```

When the user click or touch over the RadioButton a message will be logged in console showing the `value` and `selected` property values.

In __ActionScript__ we can add an event handler this way: 

```as3
var radioButton:RadioButton = new RadioButton();
radioButton.text = "A RadioButton";
radioButton.value = "somevalue";
radioButton.addEventListener('change', changeHandler);
parent.addElement(radioButton);
```

## Relevant Beads

Unlike other components in Royale, the Jewel `RadioButton` does not have beads for _View_, _Controller_ or _Model_ in the Javascript platform.

On the other hand, you can add to it other common Jewel control beads to provide more functionality. Many Jewel controls share these beads.

### Common Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [Disabled](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'}      	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | This bead lets you disable and enable a Jewel control.	|

## More examples

* [Creating a group of Jewel radio buttons](https://royale.apache.org/creating-a-group-of-jewel-radiobuttons/){:target='_blank'}

## Related controls

Other related Jewel components are:

* [CheckBox](component-sets/jewel/jewel-checkbox.html)