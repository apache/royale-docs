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
title: Jewel Themes
---

# Jewel Themes

The look and feel of the jewel component set

Jewel component set focus on themes. Themes provides the capability of change the appearance of _all_ components at once. 
A theme is a predefined CSS file (and optionally a other assets like images) that holds the definitions of each Jewel component, its subcomponents and the default [beads](welcome/features/strands-and-beads.html) used to configure that components. 

Royale use the theme to add the right css selectors to the final compilation so when the user loads the application the required css and other files are loaded and the application shows a concrete look and feel.

## Colors

Jewel comes with predefined themes based on the 12 color wheel below:

![Jewel 12 color wheel](assets/images/apache-royale-jewel-12-color-wheel.jpeg)

Current colors are:

| Color     | HEX       |
| --------- | --------- |
| Red       | #EC1C24   |
| Topaz     | #EF5A2A   |
| Orange    | #F7941D   |
| Sunflower | #F8B13F   |
| Yellow    | #E2D70B   |
| Emerald   | #8CC63C   |
| Green     | #3AB549   |
| Turquoise | #29A89F   |
| Blue      | #3CADF1   |
| Sapphire  | #2C74BE   |
| Violet    | #662C90   |
| Amethyst  | #C92CC6   |

## Light / Dark and Flat / No-Flat

Jewel has been designed to cover multiple visual needs and support Light/Dark and Flat/No Flat themes:

![Light/No Flat](assets/images/apache-royale-jewel-light-noflat.jpeg){:height="80%" width="80%"}
<br>
Light/No Flat
<br><br>
![Dark/No Flat](assets/images/apache-royale-jewel-dark-noflat.jpeg){:height="80%" width="80%"}
<br>
Dark/No Flat
<br><br>
![Light/Flat](assets/images/apache-royale-jewel-light-flat.jpeg){:height="80%" width="80%"}
<br>
Light/Flat
<br><br>
![Dark/Flat](assets/images/apache-royale-jewel-dark-flat.jpeg){:height="80%" width="80%"}
<br>
Dark/Flat
<br><br>

Jewel Themes are a CSS file in the end (`default.css`), with all needed CSS rules predefined. We create this CSSs using the __Jewel SASS Theme framework__ located in __JewelTheme__ project. By udating the rules in this theme project, we can recompile all predefined jewel themes in Apache Royale to update those themes with the latest changes.

## Predefined Jewel Themes

Jewel library has a __master theme__ called JewelTheme and other 144 themes in the `themes` folder that are generated from JewelTheme. You can know more about how this is done in the [Jewel Theme Creation](component-sets/jewel/jewel-theme-creation.html) section.

Only to name a few examples, `themes/Jewel-Dark-NoFlat-Primary-Violet-Theme` or `themes/Jewel-Light-NoFlat-Secondary-Emerald-Theme` are examples of concrete jewel themes that are part of Apache Royale official distribution. There's 144 unique themes that are the combinations of the 12 colors, dark/light and flat/no-flat options.

## Using Jewel Themes

Users will use one up to three of the predefined jewel themes in `themes` folder in a normal Application project: one for primary color, one for secondary color and one for emphasized color (i.e: `themes/Jewel-Light-NoFlat-Primary-Blue-Theme`, `themes/Jewel-Light-NoFlat-Secondary-Topaz-Theme` and finally `themes/Jewel-Light-NoFlat-Secondary-Emerald-Theme`).

Example for maven pom.xml configuration:

```xml
    <dependency>
      <groupId>org.apache.royale.framework</groupId>
      <artifactId>Jewel-Light-NoFlat-Primary-Blue-Theme</artifactId>
      <version>0.9.6-SNAPSHOT</version>
      <type>swc</type>
      <scope>theme</scope>
      <classifier>js</classifier>
    </dependency>
    <dependency>
      <groupId>org.apache.royale.framework</groupId>
      <artifactId>Jewel-Light-NoFlat-Secondary-Topaz-Theme</artifactId>
      <version>0.9.6-SNAPSHOT</version>
      <type>swc</type>
      <scope>theme</scope>
      <classifier>js</classifier>
    </dependency>
    <dependency>
      <groupId>org.apache.royale.framework</groupId>
      <artifactId>Jewel-Light-NoFlat-Emphasized-Emerald-Theme</artifactId>
      <version>0.9.6-SNAPSHOT</version>
      <type>swc</type>
      <scope>theme</scope>
    </dependency>
```

Other option is to use the __Jewel Theme Library__ that provides all styles for primary, secondary and emphasized colors and configure these colors in its `_theme.sass file`.

Example for maven pom.xml configuration:

```xml
    <dependency>
      <groupId>org.apache.royale.framework</groupId>
      <artifactId>JewelTheme</artifactId>
      <version>0.9.6-SNAPSHOT</version>
      <type>swc</type>
      <scope>theme</scope>
      <classifier>js</classifier>
    </dependency>
```