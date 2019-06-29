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
---

# Jewel

A set of modern UI components

Jewel is a themeable and responsive set of user interface components for Apache Royale to help you quickly build the front end of your applications with [ActionScript](welcome/features/as3.html) & [MXML](welcome/features/mxml.html).

It's based by design on [Basic](component-sets/basic.html) components. But while Basic is very strict with concepts like [PAYG](welcome/features/payg.html), in Jewel, while PAYG is important, when necessary we prioritize other things like responsiveness, themes and look and feel.

## Browser Support

Jewel works on the following table of devices, browsers and versions

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

| Type          	| Name                                          	| Description                                                                                          	| Available SDK 	| State     	|
|------------------	|-------------------------------------------------	|------------------------------------------------------------------------------------------------------	|---------------	|--------------	|
| __Containers__  	| Card                                           	| Container that surrounds other components                                                             	|               	|          	    |
|                	| Grid                                             	| Container that uses Grid Layout and needs other immediate children to work as cells and host content. 	|               	|          	    |
|                	| SimpleTable                                   	| A basic HTML table that can be declared in MXML                                                     	|               	| Complete      |
|                	| Table                                         	| A complex HTML table element filled from a data source. Cells are ItemRenderers.                    	|               	| In Progress   |
|                	| TabBarContent                                 	| A container to use with TabBar and capable of presenting organized content                            	|               	|           	|
|                	| Wizard                                           	| 11.0+                                                                                                	|               	|           	|
| __Components__ 	| [Alert](component-sets/jewel/jewel-alert.html)        	| Displays a message and one or more buttons in a view that pops up over all other controls and views. 	| 0.9.4         	| Complete  	|
|               	| [Button](component-sets/jewel/jewel-button.html)        	|                                                                                                      	|               	|           	|
|                 	| CheckBox                                      	|                                                                                                      	|               	|           	|
|                	| ComboBox                                      	|                                                                                                      	|               	|           	|
|                	| DateChooser                                     	|                                                                                                      	|               	|           	|
|                	| DateField                                       	|                                                                                                      	|               	|             	|
|               	| DropDownList                                  	|                                                                                                      	|               	|           	|
|               	| Form                                           	|                                                                                                      	|               	|           	|
|               	| FormItem                                      	|                                                                                                      	|               	|           	|
|                	| Icon                                            	|                                                                                                      	|               	|           	|
|               	| Image                                         	|                                                                                                      	|               	|           	|
|               	| Label                                            	|                                                                                                      	|               	|           	|
|               	| List                                             	|                                                                                                      	|               	|           	|
|               	| NumericStepper 	                                |                                                                                                      	|               	|           	|
|               	| PopUp                                          	|                                                                                                      	|               	|           	|
|               	| RadioButton                                     	|                                                                                                      	|               	|           	|
|               	| Slider                                        	|                                                                                                      	|               	|           	|
|               	| SnackBar                                         	|                                                                                                      	|               	|           	|
|               	| TabBar                                         	|                                                                                                      	|               	|           	|
|               	| [TextInput](component-sets/jewel/jewel-textinput.html)  	|                                                                                                      	|               	|           	|

## Jewel Themes

[Jewel Themes](component-sets/jewel/jewel-themes.html)