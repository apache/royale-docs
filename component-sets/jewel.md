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
title: Jewel
description: A set of modern UI components
permalink: /component-sets/jewel
---

# Jewel

A set of modern UI components

Jewel is a themeable and responsive set of [user interface](user-interface) components for [Apache Royale](https://royale.apache.org/) to help you quickly build the front end of your applications with [ActionScript](features/as3) & [MXML](features/mxml).

It's based by design on [Basic](component-sets/basic) components. But while Basic is very strict with concepts like [PAYG](features/payg), in Jewel, while PAYG is important, when necessary we prioritize other things like responsiveness, themes and look and feel.

## Browser Support

Jewel works on the following browser and device versions:

|         	    | Browser             	| Minimum Version 	| Release Date   |
|-----------	|-------------------	|-----------------	| -------------- |
| __Desktop__ 	| Google Chrome        	| 44+     	        | July,21, 2015  |
|           	| Mozilla Firefox      	| 34+     	        | Dec, 1, 2014   |
|            	| Apple Safari         	| 11.1+(High Sierra)| Feb, 22 2018   |
|            	| Microsoft Edge       	| 15+              	|                |
|            	| Microsoft IE      	| 11+             	|                |
|            	| Opera             	|               	|
| __Mobile__  	| iOS SafariMobile    	| 11.0+          	| Sep, 19, 2017  |
|             	| Android            	| 5.0            	| 2014           |
|             	| Windows Mobile    	|               	|                |

(*) This list can change depending on evolution and completion of the different components, but normally it should remain in this state.

Thanks to [Browserstack](https://www.browserstack.com){:target='_blank'} we created the list of minimum browser versions (*) where Apache Royale Jewel works consistently

## Generated JavaScript Output

For the browsers, Apache Royale generates [ECMAScript version 5 (ES5)](https://en.wikipedia.org/wiki/ECMAScript) standard JavaScript to ensure applications are compatible with a wide range of available browsers, including Microssoft Internet Explorer 11 (IE11).

## Components
If the component name is a link, you can click it to see more information about the component. We will update this list as we add information.

| Type          	| Name                                                  | Description                                                                                           | Available SDK 	| State     	|
|------------------	|------------------------------------------------------ |------------------------------------------------------------------------------------------------------ |------------------ |-------------- |
| __Containers__  	| [Application](component-sets/jewel/application)       | The root container of a Jewel Application.                                                            | 0.9.4             | Complete      |
|                 	| ApplicationMainContent                                | Container for ISelectableContent.                                                                     | 0.9.4             | Complete      |
|               	| BarRow        	                                    | A container to organize content in a row. 	                                                        | 0.9.4         	| Complete  	|
|               	| BarSection        	                                | A container to separate content and present to the user in a row. 	                                | 0.9.4         	| Complete  	|
|   	            | [Card](component-sets/jewel/card)                     | Content (text, images,...) container with optional title and actions zones.                           | 0.9.4             | Complete      |
|   	            | [Container](component-sets/jewel/container)           | Container that surrounds other components.                                                            | 0.9.4             | Complete      |
|   	            | [DataContainer](component-sets/jewel/datacontainer)   | A Container that creates child elements dynamically based on a data provider.                         | 0.9.4             | Complete      |
|   	            | [Drawer](component-sets/jewel/drawer)                 | A container used for main navigation that can optionaly be hidden to the side of screen.              | 0.9.4             | Complete      |
|               	| FooterBar        	                                    | The bottom container for main application navigation actions. 	                                    | 0.9.4         	| Complete  	|
|   	            | Form                                                  | A container to present forms to the user.                	                                            | 0.9.4             | Complete      |
|                	| [Grid](component-sets/jewel/grid)              	    | Container for responsive layout of childrens. 	                                                    | 0.9.4    	        | Complete      |
|                	| [GridCell](component-sets/jewel/gridcell)             | A cell used in Grid container. 	                                                                    | 0.9.4    	        | Complete      |
|   	            | [Group](component-sets/jewel/group)                   | The most simple container that groups other components.                 	                            | 0.9.4             | Complete      |
|   	            | [HContainer](component-sets/jewel/hcontainer)         | Container that layout other components horizontaly.                                                   | 0.9.7             | Complete      |
|   	            | [HGroup](component-sets/jewel/hgroup)                 | Group that layout other components horizontaly.                                                       | 0.9.7             | Complete      |
|                	| Module                                                | A loadable part of an Application.   	                                                                | 0.9.6    	        | Complete      |
|                	| ModuleLoader                                          | A loader for a Module.   	                                                                            | 0.9.6    	        | Complete      |
|   	            | [ResponsiveView](component-sets/jewel/responsiveview) | The main view for a responsive Application.                                                           | 0.9.4             | Complete      |
|                	| SectionContent                                        | A container to separate content and present to the user.   	                                        | 0.9.4    	        | Complete      |
|                	| ScrollableSectionContent                              | A scrollable container to separate content and present to the user.   	                            | 0.9.4    	        | Complete      |
|                	| TabBarContent                                         | A container to use with TabBar and capable of presenting organized content.                           | 0.9.4    	        | Complete      |
|               	| TopAppBar        	                                    | The top container for main application title, navigation actions. 	                                | 0.9.4         	| Complete  	|
|   	            | [VContainer](component-sets/jewel/vcontainer)         | Container that layout other components verticaly.                                                     | 0.9.7             | Complete      |
|   	            | [View](component-sets/jewel/view)                     | The main view in the Application.                                                                     | 0.9.4             | Complete      |
|   	            | [VGroup](component-sets/jewel/vgroup)                 | Group that layout other components verticaly.                                                         | 0.9.7             | Complete      |
|                	| Wizard             	                                | A container that navigates from one content to the next.                                              | 0.9.4    	        | Complete      |
| __Components__ 	| [Alert](component-sets/jewel/alert)            	    | Displays a message and one or more buttons in a view that pops up over all other controls and views. 	| 0.9.4         	| Complete  	|
|                	| BinaryImage                                           |                                                                                                      	| 0.9.7    	        | Complete	    |
|               	| [Button](component-sets/jewel/button)          	    | A commonly-used rectangular button with a text label. Users can click or tap it to take an action. 	| 0.9.4         	| Complete  	|
|                 	| [ButtonBar](component-sets/jewel/buttonbar)           | A component that displays a set of buttons                                                            | 0.9.7             | Complete      |
|                 	| IconButtonBar                                         | A component that displays a set of buttons with icons                                                 | 0.9.7             | Complete      |
|                 	| [CheckBox](component-sets/jewel/checkbox)        	    | Consists of a box that can contain a check mark and an optional label.	                            | 0.9.4         	| Complete  	|
|                	| ComboBox                                              |                                                                                                      	| 0.9.4    	        | Complete	    |
|                	| DataGrid                                              |                                                                                                      	| 0.9.7             |               |
|                	| DateChooser                                           |                                                                                                      	| 0.9.4    	        | Complete      |
|                	| DateField                                             |                                                                                                      	| 0.9.4    	        | Complete      |
|                	| Divider                                               |                                                                                                      	| 0.9.4    	        | Complete      |
|               	| DropDownList                                          |                                                                                                      	| 0.9.4    	        | Complete      |
|               	| FormHeading                                           |                                                                                                      	| 0.9.4    	        | Complete      |
|               	| FormItem      	                                    |                                                                                                      	| 0.9.4    	        | Complete      |
|               	| HSlider                                               |                                                                                                      	| 0.9.4    	        | Complete      |
|                	| Icon                	                                |                                                                                                      	| 0.9.4         	| Complete      |
|               	| IconButton          	                                | A button that can have an icon. 	                                                                    | 0.9.4             | Complete      |
|               	| Image                                                 |                                                                                                      	| 0.9.4    	        | Complete      |
|               	| [Label](component-sets/jewel/label)               	|  Used for single or multi lined text labels                                  	                        | 0.9.4    	        | Complete      |
|               	| [List](component-sets/jewel/list)                     | A data container that support selection of items.                                                     | 0.9.4    	        | Complete      |
|               	| [Navigation](component-sets/jewel/navigation)         | a List used for navigate other organized application's content                                       	| 0.9.4         	| Complete      |
|               	| NumericStepper                                        |                                                                                                      	| 0.9.4         	|               |
|               	| PopUp                                                 |                                                                                                      	| 0.9.4         	| Complete      |
|               	| [RadioButton](component-sets/jewel/radiobutton)  	    | Lets the user make a single choice within a set of mutually exclusive choices.                    	| 0.9.4             | Complete      |
|               	| VSlider                                               |                                                                                                      	| 0.9.6    	        | Complete      |
|               	| SnackBar  	   	                                    |                                                                                                      	| 0.9.4    	        | Complete      |
|                	| SimpleTable	                                        | A basic HTML table that can be declared in MXML                                                     	| 0.9.4             | Complete      |
|                	| SimpleLoader	                                        |                                                      	                                                | 0.9.7             | Complete      |
|                	| Table                                                 | A complex HTML table element filled from a data source. Cells are ItemRenderers.                    	| 0.9.4             |               |
|               	| TabBar  	                                            |                                                                                                      	| 0.9.4         	| Complete      |
|               	| TextArea        	                                    | A control for multi-line text field. 	                                                                | 0.9.4         	| Complete  	|
|               	| [TextInput](component-sets/jewel/textinput)        	| A control for single-line text field. 	                                                            | 0.9.4         	| Complete  	|
|               	| ToggleButton          	                            | A button with selected state. 	                                                                    | 0.9.4         	| Complete  	|
|                 	| ToggleButtonBar                                       | A component that displays a set of buttons that can have a selected state.                            | 0.9.7             | Complete      |
|               	| VirtualList                                           | A data container that support virtual items with selection                                          	| 0.9.7    	        |               |
|                	| VirtualComboBox                                       |                                                                                                      	| 0.9.7    	        | 	            |

## Jewel Themes

The look and feel of the jewel component set are managed by [Jewel Themes](component-sets/jewel/themes).
