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
title: Jewel Drawer
description: The Jewel Drawer
permalink: /component-sets/jewel/drawer
---
[< Jewel Components list](component-sets/jewel)

# Jewel Drawer

## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           | 
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.Drawer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Drawer){:target='_blank'} | [DrawerBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.drawer/DrawerBase){:target='_blank'} | 

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Drawer class is a container component used for navigation that can be opened with the menu icon, or be always visible. It use to be positioned at the left (or right) side of the application screen.

It can be used in __float__ or __fixed__ modes:

- __float__ make the drawer appear over the screen without make any other application elements change size. Clicking outside the drawer will hide it. Usually clicking in some navigation option will hide it as well.
- __fixed__ will need some place and make the other application content shrink. Clicking on any navigation option in the drawer usually doesn't hide it.

Drawer has other complementary components:

| Component 	     | Description                                                                                           |
|------------------- | ------------------------------------------------------------------------------------------------------|
| __DrawerHeader__   | a container to hold drawer header content (i.e: a title or an image icon logo)       				 |
| __DrawerContent__  | a container to hold drawer main content like navigation, icons, or text       						 |
| __DrawerFooter__   | a [BarRow](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.bar/BarRow){:target='_blank'} to use as the last content. Styling use to be similar to the [FooterBar](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/FooterBar){:target='_blank'}  		 |

## Example of use

In __MXML__ declare a `Drawer` like this:

```mxml
<j:Drawer>
	<j:beads>
		<j:ResponsiveDrawer auto="true"/>
	</j:beads>

	<j:DrawerHeader>
		<j:ImageButton src="assets/apache-royale-jewel-logo-white.svg"/>
	</j:DrawerHeader>

	<j:DrawerContent>
		<j:Navigation/>
		<j:Divider/>
		<j:Navigation/>
	</j:DrawerContent>

	<j:DrawerFooter>
		<j:BarSection>
			<j:Label text="Some Footer Content"/>
		</j:BarSection>
	</j:DrawerFooter>

</j:Drawer>
```

In __ActionScript__ we can do the same in the following way: 

```as3
var d:Drawer = new Drawer();
// create the DrawerContent
var dc:DrawerContent = new DrawerContent();
// add elements to DrawerContent like Navigation, Divider...
// ...and add the DrawerContent to the Drawer
d.addElement(dc);
// finally add the Drawer to the parent (usually ApplicationResponsiveView)
parent.addElement(d);
```

where `parent` is the container where the control will be added. Usually parent is [Jewel ApplicationResponsiveView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/ApplicationResponsiveView){:target='_blank'}, since Drawers are used on responsive applications.


## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.Drawer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Drawer){:target='_blank'} for a more detailed list of properties and methods.

