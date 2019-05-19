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
---
# Components

Royale provides a wide range of components to help you design a user interface that presents your material clearly and offers a pleasing user experience. As with Flex, these include:

  * Layout aids (groups, cards, grids, forms)
  * Ways to display data (lists, text boxes, tables, charts, repeating components)
  * Navigation aids (tab bars, drop-down menus, wizards, view states)
  * User-input controls (text entry fields, buttons, checkboxes, sliders)
  * Usability features (alerts, snackbar pop-ups, localization features, dynamic displays depending on the user's metadata)
  * Rich content (images, videos, audio, transitions)

Developers who have worked in Flex will quickly feel at home with Royale components, although they will need to pay attention to the ["Pay as you go"](Welcome/Features/PAYG.html) concept that is a Royale hallmark. Components do well the basic functions associated with their names, but to add features (for instance, you want to force the text the user enters to lower case), you need to add the appropriate bead to the strand of the component:

``` 
<j:TextInput text="Your entry will appear in LOWER case">
 <js:beads>
  <j:LowerCase/>
 </js:beads>
</j:TextInput>
```

You can [read more about Strands and Beads here](Welcome/Features/Strands_and_Beads.html).

## Component sets
Royale has a series of component sets, groups of ready-to-use components which are designed for different purposes.

### Basic component set
The Basic set complies strictly with the PAYG guidelines and generates the smallest amount of code so it compiles quickly.

### Express component set
The Express set is designed for rapid prototyping and proofs-of-concepts and is not optimized for size and performance. Applications built with the Express components can still be deployed in production environments if the size and performance is acceptable, which it often is.

### Jewel component set
Jewel is a little less compliant with PAYG so it can provide a great off-the-shelf look and feel. 

<a href="https://royale.apache.org/tourdejewel/" target="_blank">Tour de Jewel</a> provides working examples of Royale components styled in Jewel, with source code you can copy and paste into your own project.

### MDL component set
The MateriaDesignLite set wraps the display concepts related to <a href="https://en.wikipedia.org/wiki/Material_Design" target="_blank">Google's Material Design</a> language.

### MXRoyale/MXSpark component set
This component set seeks to emulate the functions and experience Flex developers are familiar with.

### Other component sets
There are several other component sets that are proofs-of-concept that wrap existing JavaScript frameworks. They include:

 * CreateJS
 * Flat
 * JQuery
