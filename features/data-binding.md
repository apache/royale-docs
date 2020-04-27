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
description: Update the UI in real time as data changes
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
* [Two-way data binding](features/data-binding.html#twoway)

## Using curly braces ({}) {#curly-braces}

_Details coming soon._

## Using data binding in MXML {#mxml}

_Details coming soon._
 


## Using data binding in ActionScript {#actionscript}
You can bind the value of a property in the user interface to that value of another property using the `<fx:Binding>` declaration and an ActionScript function, as in this example: 

```
<?xml version="1.0" encoding="utf-8"?>
<j:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
				xmlns:j="library://ns.apache.org/royale/jewel"
				pageTitle="Data Binding test">
	
	<fx:Script>
		<![CDATA[

			private function textInputChange(event:Event):void
			{
				textToChange.text = event.target.text;
			}		

		]]>
	</fx:Script>
	
		<fx:Binding
		source="input1.text"
		destination="textToChange.text"/>
		
		<fx:Binding
		source="input2.text"
		destination="textToChange.text"/>
	
	<j:initialView>
		<j:View width="100%" height="100%">
			<j:VGroup width="100%" height="100%" gap="5" >		
				<j:TextInput id="input1" width="300" text="" change="textInputChange(event)">
					<j:beads>
						<j:TextPrompt prompt="Type something"/>
					</j:beads>			
				</j:TextInput>
				
        <j:Label id="textToChange" text="This is a text" />	
				
			  <j:TextInput id="input2" width="300" text="" change="textInputChange(event)">
					<j:beads>
						<j:TextPrompt prompt="Type something else"/>
					</j:beads>
		    </j:TextInput >
	
			</j:VGroup>	
		</j:View>
	</j:initialView>
</j:Application>
```

Here we have two text input fields, and a single label that is bound to both of them. If you type a value into either of the input fields, the text in the label changes to match it. The label accepts the value from whichever input field you use most recently.

There are two `<fx:Binding>` declarations, one for each input field. Each declaration requires values for its source and destination properties.

The function, `textInputChange', listens for a change event on either input field and transmits the changed text to the target.

## Two-way data binding {#twoway}

_Details coming soon._
