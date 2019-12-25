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
title: Data binding
description: Data binding
permalink: /features/data-binding
---
# Data binding

Update the UI in real time as data changes

Royale, like Flex before it, makes it easy to pass data around your application. A change to data can automatically update the display of that data in the user interface, and potentially in calculations or other functions that use that data. The feature that makes this possible without having to write lots of code is *data binding*.

Data binding requires a **source property**, a **destination property**, a **triggering event** that indicates when to copy the data from the source to the destination, and a **function** to actually do the copying.

There are several ways to deploy data binding:

* [Using curly braces ({})](features/data-binding.html#curly-braces)
* [Using data binding in MXML](features/data-binding.html#mxml)
* [Using data binding in ActionScript](features/data-binding.html#actionscript)






## Using curly braces ({}) {#curly-braces}

You can bind the value of a property in the user interface to that value of another property very simply. The TextInput example in <a hred="https://royale.apache.org/tourdejewel/#" target="_blank">Tour de Jewel</a> uses data binding twice:

###Text field to text field
If you clear the existing text in the first text field in the example, then type in a string, what you type in appears in the second and fourth text fields, as you type it.

The **source property** is the text property of a TextInput control. The key part of its code is 
```
<j:TextInput text="A TextInput" change="textInputChange(event)"/>
```
When you first open the example, the control displays "A Text Input".

The **destination property** is the text property of two other TextInput controls. The ID for the first one is "textToChange", and its code looks like this:

```
<j:TextInput id="textToChange">
  <j:beads>
    <j:TextPrompt prompt="With prompt..."/>
  </j:beads>
 </j:TextInput>
 ```
 
The second destination shows a different way to bind properties. This TextInput control is disabled, but the value of its text property is bound to the "textToChange" text property value:
 
```
<j:TextInput text="{textToChange.text}">
  <j:beads>
    <j:TextPrompt prompt="Disabled with prompt..."/>
    <j:Disabled/>
  </j:beads>
</j:TextInput>
```
 
 This second destination's value won't change until the first one's does.

The **triggering event** is any change to the text property of the first control: `change="textInputChange(event)"`. 

When there's a change, the control sends an event to its change handler, _textInputChange()_, the **function** that carries out the changes. Its code looks like this:

```
private function textInputChange(event:Event):void
  {
    textToChange.text = event.target.text;
  }
```
_more to come!_

## Using data binding in MXML {#mxml}
_Details coming soon_

## Using data binding in ActionScript {#actionscript}
_Details coming soon_
