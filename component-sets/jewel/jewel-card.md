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
title: Jewel Card
description: The Jewel Card
permalink: /component-sets/jewel/card
---
[< Jewel Components list](component-sets/jewel)

# Jewel Card

## Reference

Available since version __0.9.4__.

| Class                 	    | Extends                           |
|------------------------------	|----------------------------------	|
| [org.apache.royale.jewel.Card](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Card){:target='_blank'} | [org.apache.royale.jewel.VContainer](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/VContainer){:target='_blank'} |

<sup>_Note: This component is currently only available for JavaScript._</sup>

## Overview

The Jewel Card class is a [Container](component-sets/jewel/container) for content like text or images that support optional parts like title and actions zones.

Card is a vertical container with a default "panel" styling that adds up to the features already provided by `VContainer`.

It can be use alone or with other complementary components listed below:

| Component 	             | Description                                                                                           |
|--------------------------- | ------------------------------------------------------------------------------------------------------|
| __CardHeader__             | a container to hold drawer header content (i.e: a title, image icon logo, or header actions)       	 |
| __CardTitle__              | a title label to use inside the drawer header with specific styling        				             |
| __CardPrimaryContent__     | a container to hold card main content       						                                     |
| __CardExpandedContent__    | a container for content that need to remove all paddings and gaps with the surrounding Card           |
| __CardActions__            | a footer container to hold actions like buttons, icons or navigation       						     |

## Example of use

In __MXML__ declare a `Card` like this:

```mxml
<j:Card>
    <j:CardTitle text="Jewel Simple Card"/>

    <j:Label multiline="true">
        <j:html><![CDATA[<p><Simplest version uses just the Card component laying content elements vertically with some default gap between them. It applies some default padding.</p>]]></j:html>
    </j:Label>

    <j:Button text="Action" emphasis="primary"/>
</j:Card>
```

In __ActionScript__ we can do the same in the following way: 

```as3
var card:Card = new Card();
// add a label to the Card
var label:Label = new Label();
label.text = "Some text";
card.addElement(label);
// add the Container to the parent
parent.addElement(card);
```

where `parent` is the container where the control will be added.

## Relevant Properties and Methods

> Check the Reference of [org.apache.royale.jewel.Card](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel/Card){:target='_blank'} for a more detailed list of properties and methods.

