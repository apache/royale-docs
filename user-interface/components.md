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
title: Components
description: Meet the UI building blocks.
permalink: /user-interface/components
---
# Components

Meet the UI building blocks.

[Apache Royale](https://royale.apache.org/) provides a wide range of components to help you design a [user interface](user-interface) that presents your material clearly and offers a pleasing user experience. As with Flex, these include:

  * Layout aids (groups, cards, grids, forms)
  * Ways to display data (lists, text boxes, tables, charts, repeating components)
  * Navigation aids (tab bars, drop-down menus, wizards, view states)
  * User-input controls (text entry fields, buttons, checkboxes, sliders)
  * Usability features (alerts, snackbar pop-ups, localization features, dynamic displays depending on the user's metadata)
  * Rich content (images, videos, audio, transitions)

Developers who have worked in Flex will quickly feel at home with Royale components, although they will need to pay attention to the ["Pay as you go"](features/payg) concept that is a Royale hallmark. Components do well the basic functions associated with their names, but to add features (for instance, you want to force the text the user enters to lower case), you need to add the appropriate [bead](features/strands-and-beads) to the strand of the component:

```as3 
<j:TextInput text="Your entry will appear in LOWER case">
  <j:beads>
    <j:LowerCase/>
  </j:beads>
</j:TextInput>
```

You can [read more about Strands and Beads here](features/strands-and-beads).

## Component sets

Royale has a series of [component sets](component-sets), groups of ready-to-use components which are designed for different purposes.

### Basic component set

The [Basic](component-sets/basic) set complies strictly with the PAYG guidelines and generates the smallest amount of code so it compiles quickly.

### Express component set

The Express set is Basic components with lots of Beads packed into them by default. It is designed for rapid prototyping and proofs-of-concepts and is not optimized for size and performance. Applications built with the Express components can still be deployed in production environments if the size and performance are acceptable, which is often the case.

### Jewel component set

[Jewel](component-sets/jewel) is a little less compliant with PAYG so it can provide a great off-the-shelf look and feel. 

[Tour de Jewel](https://royale.apache.org/tourdejewel){:target='_blank'} provides working examples of Royale components styled in Jewel, with source code you can copy and paste into your own project.

### MDL component set

The MateriaDesignLite set wraps the display concepts related to [Google's Material Design](https://en.wikipedia.org/wiki/Material_Design){:target='_blank'} language. This library wraps the components of [Material Design Lite](https://getmdl.io/components/index.html){:target='_blank'} library.

### MXRoyale/MXSpark component sets

This component set seeks to emulate the functions and experience Flex developers are familiar with.

### Other component sets

There are several other component sets that are proofs-of-concept that wrap existing JavaScript frameworks. They include:

 * CreateJS
 * Flat
 * JQuery
 
 ## Component sets for your application
 
 When you download the Royale SDK to your local computer, you can browse the component sets in this location: 
 
 `royale-asjsframeworks/projects`
 
 For sets that do not have an extensive demonstration suite like __Tour de Jewel__ for the __Jewel__ set, you can see quickly what components seem to be available.
 
 Let's say I then decide I want to use the Jewel component set in my application. I need to call it (and the Basic component set, as Jewel builds on some of its elements) in the opening lines of the main file in my project:
 
 ```mxml
 <?xml version="1.0" encoding="utf-8"?>
 <c:MyProjectUsingJewel xmlns:fx="http://ns.adobe.com/mxml/2009" 
  xmlns:j="library://ns.apache.org/royale/jewel">
 ```

Let's say I want to insert a multi-line label in my app's UI. I use the Label component in the "j" namespace I established for Jewel:
 
```mxml
 <j:Label text="This is a multiline label with more text that wraps if container has set a width" multiline="true"/>
```

