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
title: Styling
description: Customizing the Look and Feel of you application
permalink: /features/styling
---

# Styling

Customizing the Look and Feel of you application

Apache Royale can plug different style classes that can manage diferent levels of styling features. Usually a Royale application will compose a Style class at Application bead level like this:

```mxml
<js:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
	xmlns:js="library://ns.apache.org/royale/basic">
    ...
    <j:valuesImpl>
        <js:SimpleCSSValuesImpl />
    </j:valuesImpl>
    ...
```

## Implementations

- **SimpleCSSValuesImpl**: The SimpleCSSValuesImpl class implements a minimal set of CSS lookup rules that is sufficient for most applications and is easily implemented for SWFs. It does not support attribute selectors or descendant selectors or id selectors. It will filter on a custom `-royale-swf` media query but not other media queries. It can be replaced with other implementations that handle more complex selector lookups.

## Usign Styles

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

## Themes

In Apache Royale, a theme is a predefined CSS file (and optionally a other assets like images) that holds the definitions of each component, so adding a theme to your application or replace the existing one will make your entire application change all visuals like colors, fonts and drawings that make you components and containers looks in a certain way.

In [Jewel](component-sets/jewel) UI Set styling and themeing is one of the key concepts, you can learn more about it here:

- [Jewel Themes](component-sets/jewel/jewel-themes)