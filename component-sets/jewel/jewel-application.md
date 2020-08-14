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
title: Jewel Application
description: The Jewel Application
permalink: /component-sets/jewel/application
---
[< Jewel Components list](component-sets/jewel/application)

# Jewel Application

## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           | Implements	                    |
|------------------------------	|----------------------------------	|---------------------------------  |
| [org.apache.royale.jewel.Application](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Application){:target='_blank'} | [ApplicationBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/ApplicationBase){:target='_blank'} | [IStrand](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IStrand){:target='_blank'}, [IParent](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IParent){:target='_blank'}, [IEventDispatcher](https://royale.apache.org/asdoc/index.html#!org.apache.royale.events/IEventDispatcher){:target='_blank'}, [IInitialViewApplication](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IInitialViewApplication){:target='_blank'}, [IPopUpHost](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IPopUpHost){:target='_blank'}, [IPopUpHostParent](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IPopUpHostParent){:target='_blank'}, [IRenderedObject](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IRenderedObject){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Application class is the main class and entry point for a Royale application and does not contain user interface elements. Those UI elements go in the view ([Jewel ViewBase](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.supportClasses.view/ViewBase){:target='_blank'}). This Application class expects there to be a main __model__, a __controller__, and an __initial view__.

Jewel Application holds specific Jewel needs in a Royale Application. This class extends the standard ApplicationBase and sets up the [AllCSSValuesImpl](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/AllCSSValuesImpl){:target='_blank'} implementation for convenience.

## Example of use

In __MXML__ declare a `Application` as the root tag of the main application file like this:

```mxml
<j:Application xmlns:fx="http://ns.adobe.com/mxml/2009" 
	xmlns:j="library://ns.apache.org/royale/jewel">

    <!-- Application code goes here -->
</j:Application>
```

If the filaname is `App.mxml`, building the application will generate the following code in the `index.html` file: 

```javascript
<script type="text/javascript">
	new App().start();
</script>
```

launching the the html file in a browser will execute the Jewel Royale Application.

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.Application](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Application){:target='_blank'} for a more detailed list of properties and methods.

