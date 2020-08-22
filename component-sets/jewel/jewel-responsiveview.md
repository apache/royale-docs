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
title: Jewel View
description: The Jewel View
permalink: /component-sets/jewel/responsiveview
---
[< Jewel Components list](component-sets/jewel)

# Jewel View

## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.ResponsiveView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/ResponsiveView){:target='_blank'} | [View](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.view/View){:target='_blank'}

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The ResponsiveView class is the class used as the `initialView` in a responsive Royale Jewel [Application](component-sets/jewel/application). It is generally used as the root tag of __MXML__ documents and UI controls and containers are added to it.

It normaly can host a [TopAppBar](component-sets/jewel/topappbar), [FooterBar](component-sets/jewel/footerbar), [Drawer](component-sets/jewel/drawer) and a [ApplicationMainContent](component-sets/jewel/applicationmaincontent) with other organized content for navigation.

For non responsive applications you can use just a simple [View](component-sets/jewel/view) instead.

## Example of use

In __MXML__ declare a `ResponsiveView` like this:

```mxml
<j:ResponsiveView xmlns:fx="http://ns.adobe.com/mxml/2009" 
	xmlns:j="library://ns.apache.org/royale/jewel">

    <!-- ResponsiveView code goes here -->
</j:ResponsiveView>
```

> ResponsiveView doesn't need to specify `width` and `height` since are sized 100% in both directions by default. In this way we can use the width of the application container to apply responsive rules on any part of the application.

or directly in the application mxml fil inside the `initialView`:

```mxml
<j:Application xmlns:fx="http://ns.adobe.com/mxml/2009" 
	xmlns:j="library://ns.apache.org/royale/jewel">
	...
	<j:initialView>
		<j:ResponsiveView>
			<!-- ResponsiveView code goes here -->
		</j:ResponsiveView>
	</j:initialView>
</j:Application>
```

In __ActionScript__ we can do the same in the following way:

```as3
// instantiate the view
var responsiveView:ResponsiveView = new ResponsiveView();
// add content to the view and and add to application's initialView
application.initialView = responsiveView;
```

where `application` is the Jewel Application.

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.ResponsiveView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/ResponsiveView){:target='_blank'} for a more detailed list of properties and methods.

### Properties

| PROPERTY 	             | Type   	    | Description                                                                                           |
|----------------------- |--------------| ------------------------------------------------------------------------------------------------------|
| __applicationModel__   | _Object_ 	| A reference to the Application's model.                                               				|
| __currentState__   	 | _String_ 	| The name of the current state.                                                                        |
| __numElements__   	 | _int_ 	    | The number of element children that can be laid out.                                                  |
| __mxmlContent__   	 | _Array_ 	    | The array of childs for this view. Is the [DefaultProperty](features/as3/metadata#default-property). |
| __popUpParent__   	 | _IPopUpHostParent_ | A view can be the parent of a popup that will be part of the layout.                            |
| __popUpHost__		   	 | _IPopUpHost_ | A view can host popups that will be part of the layout.                                         		|
| __states__        	 | _Array_ 	    | The array of view states. These should be instances of [org.apache.royale.states.State](https://royale.apache.org/asdoc/index.html#!org.apache.royale.states/State){:target='_blank'}|

### Methods

| Method    	       | Parameters                                                     |Description                                            |
|----------------------|----------------------------------------------------------------|-------------------------------------------------------|
| __addElement__   	   | c(IChild), dispatchEvent(Boolean=true) 	                    | Add a component to the parent.	                    |
| __addElementAt__     | c(IChild), index(int), dispatchEvent(Boolean=true) 	        | Add a component to the parent at the specified index.	|
| __getElementIndex__  | c(IChild)                                           	        | Gets the index of this subcomponent.	                |
| __getElementAt__     | index(int)                                         	        | Get a component from the parent at specified index.	|
| __removeElement__    | c(IChild), dispatchEvent(Boolean=true) 	                    | Remove a component from the parent.	                |

## Relevant Events

The most important event is `initComplete`, which indicates that the initialization of the view is complete.

Is needed when some action coded in a callback function need to be triggered as the view is ready to use after initialization.

You can attach callback listeners to the _initComplete_ event in __MXML__ as follows:

```mxml
<j:ResponsiveView initComplete="initCompleteHandler(event)"/>
```

the _initComplete_ event will use the `initCompleteHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[      
        private function initCompleteHandler(event:Event):void {
            trace("ResponsiveView is ready!");
        }
    ]]>
</fx:Script>
```

When the view is initialized the message _"ResponsiveView is ready!"_ appears in the console log.

In __ActionScript__ we can add an event handler this way: 

```as3
var rv:ResponsiveView = new ResponsiveView();
rv.addEventListener('initComplete', initCompleteHandler);
```

## Relevant Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [GroupView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads/GroupView){:target='_blank'}      	| [org.apache.royale.core.IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'} | This is the default view bead.	|
| [ViewLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.layouts/ViewLayout){:target='_blank'}      	| [org.apache.royale.core.IBeadLayout](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadLayout){:target='_blank'} | This is the default layout bead.	|

## Optional Beads

| Bead Type       	| Implementation                               	  | Description                                     |
|-----------------	|------------------------------------------------ |------------------------------------------------	|
| [ViewDataBinding](https://royale.apache.org/asdoc/index.html#!org.apache.royale.binding/ViewDataBinding){:target='_blank'}      	| [org.apache.royale.binding.DataBindingBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.binding/DataBindingBase){:target='_blank'} | Provide binding capabilities to the view.	|

## More examples

* [Creating a Hello World in Apache Royale](https://royale.apache.org/creating-a-hello-world-in-apache-royale/){:target='_blank'}
* [Using the Jewel Alert Control](https://royale.apache.org/using-jewel-alert-control/){:target='_blank'}
* [Using View States to show or hide content](https://royale.codeoscopic.com/using-view-states-to-show-or-hide-content/){:target='_blank'}

## Related controls {#related-controls}

Other useful Jewel view components are:

* [View](component-sets/jewel/view)
* [Application](component-sets/jewel/application)
