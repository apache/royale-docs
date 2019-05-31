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
title: Jewel Alert
description: The Jewel Alert component displays a message and one or more buttons in a view that pops up over all other controls and views.
---

# Jewel Alert


## Reference

Available since version __0.9.4__

| Class                 	    | Extends                           | Implements	                    |
|------------------------------	|----------------------------------	|---------------------------------  |
| [org.apache.royale.jewel.Alert](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Alert){:target='_blank'} | [org.apache.royale.jewel.Group](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Group){:target='_blank'} | [org.apache.royale.core.IPopUp](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IPopUp){:target='_blank'} 	|

<sup>_Note: This component is currently only available in JS_</sup>

## Overview

The `Alert` component displays a message and one or more buttons in a view that pops up over all other controls and views. 
It uses the `AlertView` bead to display a [modal dialog](https://en.wikipedia.org/wiki/Modal_window){:target='_blank'} with a title and a variety of buttons configured through the flag property of its `show` static function.

> `Alert` use the HTML dialog element, which currently has very limited cross-browser support. To ensure support across all modern browsers, we use dialogPolyfill extern.

## Example of use

`Alert` is not designed to be instantiated as the majority of components. Instead, you can use the static method `show` to display the component like in the following snipet.

```as3
Alert.show('This Alert shows a label text and the default OK button.', 'Alert Example');
```

When using this way Royale generates a [modal dialog](https://en.wikipedia.org/wiki/Modal_window){:target='_blank'} that is added and centered in front of the application above the rest of displayed visual elements.

An example of `Alert` can be seen as when click the following button:

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="300" 
src="assets/BE0002_Using_Jewel_Alert_Control/index.html"></iframe>

To close the window the user can push one of the buttons in the bottom `ControlBar` or programatically call to `close` method on the instance.

## Relevant Properties and Methods

> Note: Check the Reference of [org.apache.royale.jewel.Alert](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Alert){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	    | Type   	| Description                                                                                                	|
|--------------	|----------	|-----------------------------------------------------------------------------------------------------------	|
| __title__    	| _String_ 	| The title of the `Alert`                                                                                      |
| __message__  	| _String_ 	| The message to display in the `Alert` body                                                         	        |
| __flags__    	| _uint_   	| The buttons to display on the `Alert` as bit-mask values. Possible values are: `YES`, `NO`, `OK`, `CANCEL` 	|

### Methods

| Method    	| Parameters                                                    	| Description                                                                                                                      	|
|-----------	|---------------------------------------------------------------	|----------------------------------------------------------------------------------------------------------------------------------	|
| __show__   	| _message(String), title(String), flags(uint), parent(Object)_ 	| Shows the Alert non modal anchored to the given parent object which is usally a root component such,*,as a UIView or body if null	|
| __close__  	| buttonFlag:uint = 0x000004                                    	| Closes the dialog element.                                                                                                       	|

## Events

`Alert` component uses `CloseEvent.CLOSE` event when the user removes it from the application. You can attach callback listeners to the `CloseEvent.CLOSE` as follows:

```as3
var alert:Alert = Alert.show("Do you want to save your changes?", "Save Changes", Alert.OK);
alert.addEventListener(CloseEvent.CLOSE, alertClickHandler);
```

Then check  `event.detail` to know what button was clicked inside the dialog.

```as3
// Event handler callback function for CloseEvent event 
private function alertClickHandler(event:CloseEvent):void {
    if (event.detail == Alert.YES)
        status.text="You answered Yes";
    else
        status.text="You answered No";
}
```

## Beads

The `Alert` component uses the following beads:

| Bead Type       	| Implementation                                            	| Description                                    	|
|-----------------	|-----------------------------------------------------------	|------------------------------------------------	|
| [IBeadModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadModel){:target='_blank'}      	| [org.apache.royale.jewel.beads.models.AlertModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.models/AlertModel){:target='_blank'}           	| The data model for the Alert                   	|
| [IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'}       	| [org.apache.royale.jewel.beads.views.AlertView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.views/AlertView){:target='_blank'}           	| The bead used to create the parts of the Alert 	|
| [IBeadController](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadController){:target='_blank'} 	| [org.apache.royale.jewel.beads.controllers.AlertController](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controllers/AlertController){:target='_blank'} 	| The bead used to handle input events           	|
| [IBeadLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadLayout){:target='_blank'}     	| [org.apache.royale.jewel.beads.layouts.NullLayout](){:target='_blank'}<sup>_(*)_</sup>  | The bead used to postion the internal parts       |

<sup>_(*) NullLayout is used temporary_</sup>

