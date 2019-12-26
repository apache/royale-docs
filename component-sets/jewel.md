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

Jewel is a themeable and responsive set of user interface components for Apache Royale to help you quickly build the front end of your applications with [ActionScript](features/as3) & [MXML](features/mxml).

It's based by design on [Basic](component-sets/basic) components. But while Basic is very strict with concepts like [PAYG](features/payg), in Jewel, while PAYG is important, when necessary we prioritize other things like responsiveness, themes and look and feel.

## Browser Support

Jewel works on the following browser and device versions:

|         	    | Browser             	| Minimun Version 	| Release Date   |
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

## Generated Javascript Output

For the browsers, Apache Royale generates [ECMAScript version 5 (ES5)](https://en.wikipedia.org/wiki/ECMAScript) standard JavaScript to ensure applications are compatible with a wide range of available browsers, including Microssoft Internet Explorer 11 (IE11).

## Components

| Type          	| Name                       | Description                                                                    	| Available SDK 	| State     	|
|------------------	|--------------------------- |--------------------------------------------------------------------------------- |------------------ |--------------	|
| __Containers__  	| [ButtonBar](component-sets/jewel/buttonbar)              	    |                                                              	| 0.9.7              	| Complete         	    |
|   	| [Card](component-sets/jewel/card)              	    | Container that surrounds other components                                                             	| 0.9.4              	|          	    |
|                	| [Grid](component-sets/jewel/grid)              	    | Container that uses Grid Layout and needs other immediate children to work as cells and host content. 	| 0.9.4    	| Complete |
|                	| [SimpleTable](component-sets/jewel/simpletable)	    | A basic HTML table that can be declared in MXML                                                     	| 0.9.4              	| Complete      |
|                	| [Table](component-sets/jewel/table)                    | A complex HTML table element filled from a data source. Cells are ItemRenderers.                    	| 0.9.4              	| In Progress   |
|                	| [TabBarContent](component-sets/jewel/tabbarcontent)    | A container to use with TabBar and capable of presenting organized content                            	| 0.9.4    	| Complete |
|                	| [Wizard](component-sets/jewel/wizard)             	    | 11.0+                                                                                                	| 0.9.4    	| Complete |
| __Components__ 	| [Alert](component-sets/jewel/alert)            	    | Displays a message and one or more buttons in a view that pops up over all other controls and views. 	| 0.9.4         	| Complete  	|
|               	| [Button](component-sets/jewel/button)          	    | A commonly-used rectangular button with a text label. Users can click or tap it to take an action. 	| 0.9.4         	| Complete  	|
|               	| [ButtonBar](component-sets/jewel/buttonbar)          	    |  	| 0.9.7         	| Complete  	|
|                 	| [CheckBox](component-sets/jewel/checkbox)        	    | Consists of a box that can contain a check mark and an optional label.	| 0.9.4         	| Complete  	|
|                	| [ComboBox](component-sets/jewel/combobox)              |                                                                                                      	| 0.9.4    	| Complete	|
|                	| [DataGrid](component-sets/jewel/datagrid)        |                                                                                                      	|  0.9.7             	|           	|
|                	| [DateChooser](component-sets/jewel/datechooser)        |                                                                                                      	| 0.9.4    	| Complete |
|                	| [DateField](component-sets/jewel/datefield)            |                                                                                                      	| 0.9.4    	| Complete |
|               	| [DropDownList](component-sets/jewel/dropdownlist)      |                                                                                                      	| 0.9.4    	| Complete |
|               	| [Form](component-sets/jewel/form)                      |                                                                                                      	| 0.9.4    	| Complete |
|               	| [FormItem](component-sets/jewel/formitem)      	    |                                                                                                      	| 0.9.4    	| Complete |
|                	| [Icon](component-sets/jewel/icon)                	    |                                                                                                      	| 0.9.4    	| Complete |
|               	| [Image](component-sets/jewel/image)                    |                                                                                                      	| 0.9.4    	| Complete |
|               	| [Label](component-sets/jewel/label)               	    |  Used for single or multi lined text labels                                  	| 0.9.4    	| Complete	|
|               	| [List](component-sets/jewel/list)               	    |                                                                                                      	| 0.9.4    	| Complete |
|               	| [NumericStepper](component-sets/jewel/numericstepper)  |                                                                                                      	| 0.9.4               	|           	|
|               	| [PopUp](component-sets/jewel/popup)                    |                                                                                                      	| 0.9.4    	| Complete |
|               	| [RadioButton](component-sets/jewel/radiobutton)  	    | Lets the user make a single choice within a set of mutually exclusive choices	| 0.9.4         	| Complete  	|
|               	| [HSlider](component-sets/jewel/hslider)                  |                                                                                                      	| 0.9.4    	| Complete |
|               	| [VSlider](component-sets/jewel/vslider)                  |                                                                                                      	| 0.9.6    	| Complete |
|               	| [SnackBar](component-sets/jewel/snackbar)  	   	    |                                                                                                      	| 0.9.4    	| Complete |
|               	| [TabBar](component-sets/jewel/tabbar)  	            |                                                                                                      	| 0.9.4    	| Complete |
|               	| [TextInput](component-sets/jewel/textinput)        	| A control for single-line text field. 	| 0.9.4         	| Complete  	|

## Jewel Themes

[Jewel Themes](component-sets/jewel/jewel-themes)
