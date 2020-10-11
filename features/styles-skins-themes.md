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
title: Styles, skins and themes
description: Customizing the look and feel of your application
permalink: /features/styles-skins-themes
---

# Styles, skins and themes

Customizing the look and feel of your application

Royale provides three features for adjusting the look and feel of your application: styles, skins, and themes.

## Styles

You can plug different style classes into your Royale app that can manage different levels of styling features. Usually a Royale application will include a Style class at the Application bead level like this:

```mxml
<js:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
	xmlns:js="library://ns.apache.org/royale/basic">
    ...
    <j:valuesImpl>
        <js:SimpleCSSValuesImpl />
    </j:valuesImpl>
    ...
```

### Implementations

- **SimpleCSSValuesImpl**: The SimpleCSSValuesImpl class implements a minimal set of CSS lookup rules that is sufficient for most applications and is easily implemented for SWFs. It does not support attribute selectors, descendant selectors, or id selectors. It filters on a custom `-royale-swf` media query but not other media queries. You can replace it in your app with other implementations that handle more complex selector lookups.

### Using Styles

- **SimpleCSSStyles**: Brings simple styles to Royale.

```mxml
<js:VContainer id="vb" width="100%" height="100%">
    <js:style>
        <js:SimpleCSSStyles paddingLeft="6" paddingTop="4" paddingRight="8" paddingBottom="4"/>
    </js:style>
</js:VContainer>
```

- **SimpleCSSStylesWithFlex**: Tries to support Flex styling properties.

```mxml
<js:PanelView>
    <js:titleBar>
        <js:TitleBar height="20">
            <js:style>
                <js:SimpleCSSStylesWithFlex backgroundColor="0xA65904" />
            </js:style>
        </js:TitleBar>
    </js:titleBar>
</js:PanelView>
```

## Skins

Skinning is a technique to change the appearance of a component by modifying or extending its visual elements. Skins can have graphical elements like images, or can use ActionScript classes that use the drawing API.

_More information on skinning, with examples, is coming soon._

## Themes

In Apache Royale, a theme is a predefined CSS file (and optionally other assets like images) that holds the definitions of each component. When you add a theme to your application or replace the existing one, all the visuals (colors, fonts, lines, and drawings) in your your entire application change to the new theme at once.

In the [Jewel](component-sets/jewel) UI Set, themeing is one of the key concepts. You can learn more about it here: [Jewel Themes](component-sets/jewel/jewel-themes).
