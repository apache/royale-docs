---
# Licensed to the Apache Software Foundation (ASF) under one or more contributor license agreements.  See the NOTICE file distributed with this work for additional information regarding copyright ownership. The ASF licenses this file to You under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License.  You may obtain a copy of the License at
# 
# http://www.apache.org/licenses/LICENSE-2.0
# 
# Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
layout: docpage
title: Flex equivalents in Royale
---

Moving from Flex to Royale

# Flex equivalents in Royale
Royale is not a one-for-one migration of Flex, for several reasons. A lot of Flex code presumes, and takes advantage of, features available in the Adobe AIR environment or the Flash Player plugin. Other Flex elements are more bulky than they could best be as they try to cover a wide range of possible events and situations, so a great deal of the code in an application may be there "just in case" and is never actually used.

Moving from Flex to Royale is straightforward for most of your application's functions, such as getting and manipulating data, performing calculations, and moving objects through their life cycles in the application. However, some Flex features, especially among UI components and functions, do not have direct Royale equivalents.

As they become available, we will provide code snippets, examples, and full tutorials to help you with the trickier parts of your migration to Royale.

## Flex features you can achieve in a different way in Royale
_This list is growing as people migrating Flex applications run into features and functions they need, but Royale does not yet support._

- **[View States](/features/view-states)** is  a super feature that lets you include or exclude components based on the current state of the application. For example, a registration/login form could have different fields and controls depending on whether the current state was "register" or "login". In Flex you could declare States (and make other declarations) in the application level, and then use those states for all the components of the application. In Royale the earliest component where you can have such declarations is View. In general you can declare States in every component which inherits from UIBase. <js:Application doesn't inherit from UIBase.
- **Embedding assets** was necessary in Flex so the application could quickly access images and other assets that were part of a compiled Flash SWF. To make it easy to display on a button an icon that was in a SWF, we wrote something like:
 `<mx:Button icon="@Embed('icons.swf#our_button')"/>`
Since JavaScript does not support the concept of embedding assets, doing the same thing in Royale is a simple URL reference:
 `<mx:Button icon="icons/our_button.png"/>` (once you have placed the relevant image in the _icons_ folder).
- PopUpManager
- BorderContainer - using UIBase
- Advanced DataGrid - TreeGrid
- Canvas
- Routing: in Flex this was called "deep linking". This allowed changing the URL to use browser history to navigate an application.

## Flex features that are not yet available in Royale

- TitleWindow
- Menu and MenuBar
- VariableRowHeight
- Editable DataGrids
- Sorting within DataGrids
- Handling of SVG (graphics) assets.
- Masking of images and objects.
- Image components which allow specifying content via raw binary data or the image's URL.
- File transfer API.
- Font and text handling.
- UID utilities.
- Transformations.
- Color filters and transforms.
- Cursor Manager

## Flex features that will probably not be available in Royale

- Timeline and onEnterFrame
- Embedding assets (not needed in Royale, as explained above)

