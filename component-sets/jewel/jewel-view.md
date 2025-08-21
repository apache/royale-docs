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
permalink: /component-sets/jewel/view
---
[< Jewel Components list](component-sets/jewel)

# Jewel View

## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           | Implements	                    |
|------------------------------	|----------------------------------	|---------------------------------  |
| [org.apache.royale.jewel.View](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/View){:target='_blank'} | [ViewBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.view/ViewBase){:target='_blank'} | [IMXMLDocument](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IMXMLDocument){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The View class is used as the `initialView` in a Royale Jewel [Application](component-sets/jewel/application). It is generally used as the root tag of __MXML__ documents and UI controls and containers are added to it.

For responsive applications you can use [ResponsiveView](component-sets/jewel/responsiveview) instead.

## Example of use

In __MXML__ declare a `View` like this:

```mxml
<j:View xmlns:fx="http://ns.adobe.com/mxml/2009" 
    xmlns:j="library://ns.apache.org/royale/jewel"
    width="100%" height="100%">

    <!-- View code goes here -->
</j:View>
```

or directly in the application mxml file inside the `initialView`:

```mxml
<j:Application xmlns:fx="http://ns.adobe.com/mxml/2009" 
    xmlns:j="library://ns.apache.org/royale/jewel">
    ...
    <j:initialView>
        <j:View width="100%" height="100%">
            <!-- View code goes here -->
        </j:View>
    </j:initialView>
</j:Application>
```

In __ActionScript__ we can do the same in the following way:

```as3
// instantiate the view
var view:View = new View();
// add content to the view and and add to application's initialView
application.initialView = view;
```

where `application` is the Jewel Application.

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.View](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/View){:target='_blank'} for a more detailed list of properties and methods.

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

It is needed when some action coded in a callback function needs to be triggered when the view is ready to use after initialization.

You can attach callback listeners to the _initComplete_ event in __MXML__ as follows:

```mxml
<j:View initComplete="initCompleteHandler(event)"/>
```

the _initComplete_ event will use the `initCompleteHandler` callback function you provide in __ActionScript__:

```mxml
<fx:Script>
    <![CDATA[      
        private function initCompleteHandler(event:Event):void {
            trace("View is ready!");
        }
    ]]>
</fx:Script>
```

When the view is initialized the message _"View is ready!"_ appears in the console log.

In __ActionScript__ we can add an event handler this way: 

```as3
var v:View = new View();
v.addEventListener('initComplete', initCompleteHandler);
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

### Common Beads

Jewel `View` can use any of the layout beads available in the Jewel library. You can also check [Related controls](component-sets/jewel/view.html#related-controls) to see some preconfigured views with specific layouts.

## More examples

* [Creating a Hello World in Apache Royale](https://royale.apache.org/creating-a-hello-world-in-apache-royale/){:target='_blank'}
* [Using the Jewel Alert Control](https://royale.apache.org/using-jewel-alert-control/){:target='_blank'}
* [Using View States to show or hide content](https://royale.codeoscopic.com/using-view-states-to-show-or-hide-content/){:target='_blank'}

## Related controls {#related-controls}

Other useful Jewel view components are:

* [ResponsiveView](component-sets/jewel/responsiveview)
* [Application](component-sets/jewel/application)
