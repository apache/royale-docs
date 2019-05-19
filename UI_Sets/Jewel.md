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

Jewel is a themeizable and responsive set of user interface components for Apache Royale to quickly build Front-end Applications with [ActionScript](Welcome/Features/AS3.html) & [MXML](Welcome/Features/MXML.html).

It's based by design on [Basic](UI_Sets/Basic.html) components but while Basic is very strict with concepts like [PAYG](Welcome/Features/PAYG.html), in Jewel they are important but when it is necessary, we prioritize other things like responsiveness, themes and look and feel.

## Browser Support

Jewel works on the following table of devices, browsers and versions

|         	    | Browser             	| Minimun Version 	|
|-----------	|-------------------	|-----------------	|
| __Desktop__ 	| Google Chrome        	| 44+     	        |
|           	| Mozilla Firefox      	| 34+     	        |
|            	| Apple Safari         	| 11.1+         	|
|            	| Microsfot Edge       	| 15+              	|
|            	| Microsfot IE      	| 11+             	|
|            	| Opera             	|               	|
| __Mobile__  	| iOS SafariMobile    	| 11.0+          	|
|             	| Android            	| 5.0            	|
|             	| Windows Mobile    	|               	|

## Generated Javascript Output

In the browsers, Apache Royale generates [ECMAScript version 5 (ES5)](https://en.wikipedia.org/wiki/ECMAScript) standard Javascript to ensure applications are compatible with a great set of available browsers, including Microssoft Internet Explorer 11 (IE11).

## Components

| Type          	| Name                                          	| Description                                                                                          	| Available SDK 	| State     	|
|------------------	|-------------------------------------------------	|------------------------------------------------------------------------------------------------------	|---------------	|--------------	|
| __Containers__  	| Card                                           	| Container that surronds other components                                                             	|               	|          	    |
|                	| Grid                                             	| Container that uses Grid Layout and need other immediate children to work as cells and host content. 	|               	|          	    |
|                	| SimpleTable                                   	| An Basic HTML Table that can be declared in MXML                                                     	|               	| Finished      |
|                	| Table                                         	| An Complex HTML Table element filled with a data source. Cells are ItemRenderers.                    	|               	| In Progress   |
|                	| TabBarContent                                 	| A Container to use with TabBar and capable of parenting organized content                            	|               	|           	|
|                	| Wizard                                           	| 11.0+                                                                                                	|               	|           	|
| __Components__ 	| [Alert](UI_Sets/Jewel/Jewel-Alert.html)        	| Displays a message and one or more buttons in a view that pops up over all other controls and views. 	| 0.9.4         	| Finished  	|
|               	| [Button](UI_Sets/Jewel/Jewel-Button.html)        	|                                                                                                      	|               	|           	|
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
|               	| [TextInput](UI_Sets/Jewel/Jewel-TextInput.html)  	|                                                                                                      	|               	|           	|
