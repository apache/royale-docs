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
title: Template for component details
description: This is a template for the details pages for components
permalink: /component-sets/jewel/alert
---
[< Jewel Components list](component-sets/jewel)

# Component set and Name of Component


## Reference
Available since version __VERSION NUMBER__

| Class                 	    | Extends                           | Implements	                    |
|------------------------------	|----------------------------------	|---------------------------------  |
|  |  |  	|

<sup>_Note: This component is currently only available in JavaScript_</sup>.

## Overview

_Overview text here_

## Example of use

_how to use it goes here_

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.SET.NAME](){:target='_blank'} for a more detailed list of properties and methods.

_the contents below are for the Jewel Alert. Update them for this component._
### Properties

| PROPERTY 	    | Type   	| Description                                                                                                	|
|--------------	|----------	|-----------------------------------------------------------------------------------------------------------	|
| __title__    	| _String_ 	| The title of the `Alert`.                                                                                      |
| __message__  	| _String_ 	| The message to display in the `Alert` body.                                                        	        |
| __flags__    	| _uint_   	| The buttons to display on the `Alert` as bit-mask values. Possible values are: `YES`, `NO`, `OK`, and `CANCEL`. 	|

### Methods

| Method    	| Parameters                                                    	| Description                                                                                                                      	|
|-----------	|---------------------------------------------------------------	|----------------------------------------------------------------------------------------------------------------------------------	|
| __show__   	| _message(String), title(String), flags(uint), parent(Object)_ 	| Shows the Alert non modal anchored to the given parent object, which is usally a root component such as *, as a UIView or body if null.	|
| __close__  	| buttonFlag:uint = 0x000004                                    	| Closes the dialog element.                                                                                                       	|

## Relevant Events

The `Alert` component uses the `CloseEvent.CLOSE` event when the user removes it from the application. You can attach callback listeners to the `CloseEvent.CLOSE` as follows:

```as3
var alert:Alert = Alert.show("Do you want to save your changes?", "Save Changes", Alert.OK | Alert.NO);
alert.addEventListener(CloseEvent.CLOSE, alertClickHandler);
```

Then check `event.detail` to know what button was clicked inside the dialog.

```as3
// Event handler callback function for CloseEvent event 
private function alertClickHandler(event:CloseEvent):void {
    if (event.detail == Alert.YES)
        status.text="You answered Yes";
    else
        status.text="You answered No";
}
```

## Relevant Beads

The `Alert` component uses the following beads:

| Bead Type       	| Implementation                                            	| Description                                    	|
|-----------------	|-----------------------------------------------------------	|------------------------------------------------	|
| [IBeadModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadModel){:target='_blank'}      	| [org.apache.royale.jewel.beads.models.AlertModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.models/AlertModel){:target='_blank'}           	| The data model for the Alert.                   	|
| [IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'}       	| [org.apache.royale.jewel.beads.views.AlertView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.views/AlertView){:target='_blank'}           	| The bead used to create the elements of the Alert. 	|
| [IBeadController](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadController){:target='_blank'} 	| [org.apache.royale.jewel.beads.controllers.AlertController](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controllers/AlertController){:target='_blank'} 	| The bead used to handle input events.           	|
| [IBeadLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadLayout){:target='_blank'}     	| [org.apache.royale.jewel.beads.layouts.NullLayout](){:target='_blank'}<sup>_(*)_</sup>  | The bead used to postion the elements of the Alert.       |

<sup>_(*) NullLayout is used temporarily_.</sup>

