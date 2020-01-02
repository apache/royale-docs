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
title: Jewel TextInput
description: The Jewel TextInput is a control for single-line text field
permalink: /component-sets/jewel/textinput
---
[< Jewel Components list](component-sets/jewel)

# Jewel TextInput


## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.TextInput](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/TextInput){:target='_blank'} | [org.apache.royale.jewel.supportClasses.textinput.TextInputBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.textinput/TextInputBase){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel TextInput implements the jewel control for single-line text field. It dispatches a change event when the user input text.

> For multi line text input control see [TextArea](component-sets/jewel/textarea)

## Example of use

In __MXML__ declare a `TextInput` like this:

```mxml
<j:TextInput/>
```

In __ActionScript__ we can do the same in the following way: 

```as3
var textInput:TextInput = new TextInput();
parent.addElement(textInput);
```

where `parent` is the container where the control will be added.

Here is an example of the default text input:

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="300" 
src="assets/jewel/jewel_textinput/index.html"></iframe>

[code here](https://github.com/apache/royale-docs/blob/master/assets/jewel/jewel_textinput/jewel_textinput.mxml){:target='_blank'}

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.TextInput](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/TextInput){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	    | Type   	| Description                                                                   |
|--------------	|----------	| -----------------------------------------------------------------------------	|
| __text__    	| _String_ 	| The text inside the text field.                                            |
| __html__  	| _String_ 	| The html text inside the text field.                                       |

### Methods

None.

## Relevant Events

The `TextInput` has _change_ event of type [org.apache.royale.events.Event](https://royale.apache.org/asdoc/index.html#!org.apache.royale.events/Event){:target='_blank'}. This event is dispatched when text in the control changes through user input. Notice that programatic changes will not trigger this event.

You can attach callback listeners to the _change_ event in __MXML__ as follows:

```mxml
<j:TextInput change="changeHandler(event)"/>
```

the _change_ event will use the `changeHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[      
        private function changeHandler(event:Event):void {
            trace("new text is: " + event.target.text);
        }
    ]]>
</fx:Script>
```

When the user introduce text in the input field, the message _"new text is: "_ plus the text introduced will appear in the console log.

In __ActionScript__ we can add an event handler this way: 

```as3
var textInput:TextInput = new TextInput();
textInput.addEventListener('change', changeHandler);
parent.addElement(textInput);
```

## Relevant Beads

Unlike other components in Royale, the Jewel `TextInput` does not have beads for _View_, _Controller_ or _Model_ in the Javascript platform.

On the other hand, you can add to it beads specialy crafted for this control or other common Jewel control beads (shared with other controls) to provide more functionality.

### TextInput Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [LowerCase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/LowerCase){:target='_blank'} 	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to makes all text change to lower case.           	|
| [MaxNumberCharacters](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/MaxNumberCharacters){:target='_blank'} 	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to set the maximun number of characters the text field can hold.           	|
| [PasswordInput](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/PasswordInput){:target='_blank'} 	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to secures the text field by masking the input as it is typed. 	|
| [Restrict](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/Restrict){:target='_blank'}     	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to use a regular expresion pattern to validate input from user. |
| [SearchFilterForList](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/SearchFilterForList){:target='_blank'}      	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to filter options in other [Jewel List](component-sets/jewel/list) component used in combo with the text input.	|
| [TextPrompt](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/TextPrompt){:target='_blank'}     	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to place a string into the input field when there is no value associated with the text property. |
| [UpperCase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/UpperCase){:target='_blank'}       	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to makes all text change to upper case.  	|

### Common Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [Disabled](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'}      	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | This bead lets you disable and enable a Jewel control.	|
| [SizeControl](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/SizeControl){:target='_blank'} 	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to give the Jewel control a custom size.           	|
| [ToolTip](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/ToolTip){:target='_blank'}     	| [org.apache.royale.core.IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} | Add this bead to enable floating a text string over the control when the user hovers the mouse cursor over it. |

## More examples

* [Binding the text property of a Jewel TextInput to update a text Label](https://royale.apache.org/binding-the-text-property-of-a-jewel-textinput-to-update-a-text-label/){:target='_blank'}
* [Using View States to show or hide content](https://royale.apache.org/using-view-states-to-show-or-hide-content/){:target='_blank'}
* [Dividing an Apache Royale application with modules](https://royale.apache.org/dividing-an-apache-royale-application-with-modules/){:target='_blank'}

## Related controls

Other related Jewel components are:

* [TextArea](component-sets/jewel/textarea)
