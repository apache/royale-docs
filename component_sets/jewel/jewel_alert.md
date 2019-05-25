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
---

# Jewel Alert

org.apache.royale.jewel.Alert

|            	| ALL                           	| JS 	| SWF 	|
|------------	|-------------------------------	|----	|-----	|
| extends    	| org.apache.royale.jewel.Group 	| -  	| -   	|
| implements 	| org.apache.royale.core.IPopUp 	|    	|     	|

Note: This component is currently only available in JS

Available since 0.9.4

## Overview

The alert component displays a message and one or more buttons in a view that pops up over all other controls and views. 
It uses the `AlertView` bead to display a modal dialog with a title and a variety of buttons configured through the flag property of its `show` static function.

## Examples

You can use the static method `show` to display the component:

    Alert.show('This is an Alert component example that shows a label text and the default OK button.', 'Alert Example')

This produces:

{% raw %}
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="300" 
src="assets/BE0002_Using_Jewel_Alert_Control/index.html"></iframe>
{% endraw %}

You can attach listeners to the CloseEvent.CLOSE as follows:

    var alert:Alert = Alert.show("Do you want to <b>save</b> your changes?", "Save Changes", 3);
	alert.addEventListener(CloseEvent.CLOSE, alertClickHandler);


Alert use the HTML dialog element, which currently has very limited cross-browser support.
To ensure support across all modern browsers, we use dialogPolyfill extern.

## Beads

The Alert component uses the following beads:

| Bead Type       	| Implementation                                            	| Description                                    	|
|-----------------	|-----------------------------------------------------------	|------------------------------------------------	|
| IBeadModel      	| org.apache.royale.jewel.beads.models.AlertModel           	| the data model for the Alert                   	|
| IBeadView       	| org.apache.royale.jewel.beads.views.AlertView             	| the bead used to create the parts of the Alert 	|
| IBeadController 	| org.apache.royale.jewel.beads.controllers.AlertController 	| the bead used to handle input events           	|
| IBeadLayout     	| org.apache.royale.jewel.beads.layouts.NullLayout(*)       	| the bead used to postion the internal parts       |


(*) NullLayout is used temporary