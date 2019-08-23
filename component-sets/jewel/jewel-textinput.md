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

---

# Jewel TextInput


## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.TextInput](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/TextInput){:target='_blank'} | [org.apache.royale.jewel.supportClasses.textinput.TextInputBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.textinput/TextInputBase){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel TextInput implements the jewel control for single-line text field. It dispatches a change event when the user input text.

> For multi line text input control see [TextArea](component-sets/jewel/jewel-textarea.html)

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

Here is an example of the default button:

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

TODO