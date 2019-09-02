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
title: Jewel CheckBox
description: The Jewel CheckBox consists of a selectable box, that can contain a check mark or not, and an optional label.
permalink: /component-sets/jewel/checkbox
---

# Jewel CheckBox

## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.CheckBox](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/CheckBox){:target='_blank'} | [org.apache.royale.jewel.supportClasses.button.SelectableButtonBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.button/SelectableButtonBase){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel CheckBox consists of a selectable box, that can contain a check mark, and an optional label. When a user clicks or touches this control or its associated text, the CheckBox changes its state from checked to unchecked or from unchecked to checked, communicating clearly a binary condition. Checkboxes can appear alone or in groups, and can be selected and deselected individually.

## Example of use

In __MXML__ declare a `CheckBox` like this:

```mxml
<j:CheckBox/>
```

In __ActionScript__ we can do the same in the following way: 

```as3
var checkBox:CheckBox = new CheckBox();
parent.addElement(checkBox);
```

where `parent` is the container where the control will be added.

Here is an example for this control:

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="300" 
src="assets/jewel/jewel_checkbox/index.html"></iframe>

[code here](https://github.com/apache/royale-docs/blob/master/assets/jewel/jewel_checkbox/jewel_checkbox.mxml){:target='_blank'}

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.CheckBox](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/CheckBox){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	    | Type   	| Description                                                                   |
|--------------	|----------	| -----------------------------------------------------------------------------	|
| __selected__  | _Boolean_ | `true` if the check mark is displayed, `false` otherwise.                     |
| __text__  	| _String_ 	| The string used as a label.                                                   |
| __value__     | _String_  | The associated value.                                                         |

### Methods

None.

## Relevant Events

The `CheckBox` has a _change_ event of type [org.apache.royale.events.Event](https://royale.apache.org/asdoc/index.html#!org.apache.royale.events/Event){:target='_blank'}. This event is dispatched when the control is selected or deselected by the user. Notice that Programmatic changes will not trigger this event.

Since this component is in essence a button, it has a _click_ event as well. When the user clicks the control it dispatches a normal _click_ event.

You can attach callback listeners to the _change_ event in MXML as follows:

```mxml
<j:CheckBox text="A Checkbox" value="50" change="changeHandler(event)"/>
```

the _change_ event will use the `changeHandler` callback function you provide in ActionScript:

```as3
<fx:Script>
    <![CDATA[
        private function changeHandler(event:Event):void {
            trace('CheckBox value is: ' + event.target.value, ' and selected state is: ' + event.target.selected);
        }
    ]]>
</fx:Script>
```

When the user clicks or presses the CheckBox a message will be logged in the console showing the `value` and `selected` property values.

In ActionScript we can add an event handler this way: 

```as3
var checkBox:CheckBox = new CheckBox();
checkBox.text = "A CheckBox";
checkBox.value = 50;
checkBox.addEventListener('change', changeHandler);
parent.addElement(checkBox);
```

## Relevant Beads

Unlike other components in Royale, the Jewel `CheckBox` does not have beads for _View_, _Controller_ or _Model_ in the Javascript platform.

On the other hand, you can add to it other common Jewel control beads to provide more functionality. Many Jewel controls share these beads.

### Common Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [Disabled](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'}      	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | This bead lets you disable and enable a Jewel control.	|

## More examples

* [Selecting options from a group of Jewel CheckBox controls](https://royale.apache.org/selecting-options-from-a-group-of-jewel-checkbox-controls/){:target='_blank'}

## Related controls

Other related Jewel components are:

* [RadioButton](component-sets/jewel/radiobutton)
