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
title: MXML
description: The declarative XML-based user interface markup language
permalink: /features/mxml
---

# MXML

The declarative XML-based user interface markup language

MXML is an XML-based language introduced in 2004 by Macromedia. In Royale you use it to lay out user-interface components. You can create an application in Royale using only [ActionScript](features/as3), but it takes a lot more work.

Most Royale applications have an MXML file as the main file. It provides the structure of the application. The main MXML file from our very simple <a href="https://apache.github.io/royale-docs/get-started/hello-world" target="_blank">hello world example</a> looks a bit like this:

```
<?xml version="1.0" encoding="utf-8"?>

</-- 
   A comments field that could include a copyright statement, license notice, author notice, 
   a statement of the purpose of the file, and 
   other information useful for future file maintenance.
-->

<js:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
                xmlns:js="library://ns.apache.org/royale/express">

    <js:initialView>
        <js:View>
            <js:Label text="Hello World" />
        </js:View>
    </js:initialView>
</js:Application>
```

You also build components that you might incorporate into an application using an MXML file. A component with a card layout to display a set of clickable buttons might look like this:

```
<?xml version="1.0" encoding="utf-8"?>

</-- 
   A comments field that could include a copyright statement, license notice, author notice, 
   a statement of the purpose of the file, and 
   other information useful for future file maintenance.
-->

<j:Group xmlns:fx="http://ns.adobe.com/mxml/2009" 
        xmlns:j="library://ns.apache.org/royale/jewel" 
        xmlns:html="library://ns.apache.org/royale/html">

    <fx:Script>
    <![CDATA[      
        private function clickHandler(event:MouseEvent):void {
            button.emphasis = (button.emphasis == Button.PRIMARY) ? "" : Button.PRIMARY;
        }
    ]]>
    </fx:Script>

    <j:Card width="600">
        <html:H3 text="items expand test"/>

        <j:HGroup itemsExpand="true" gap="3">
            <j:Button text="Hello" click="clickHandler(event)"/>
            <j:Button text="Apache"/>
            <j:Button text="Royale!!!!"/>
        </j:HGroup>
    </j:Card>
</j:Group>
```

## What goes where ##

The more complex the application is, the more things the main MXML file needs to be able to support and do. Typically, a developer organizes the file so it is easy to locate things in it. Some elements must be inside certain tags, and for others you have a lot of flexibility. However, if you are working in a team, it is good to have an agreement about what goes where so nobody wastes time or tries to add code that already exists somewhere else in the file.

### What your file _must_ have ###

Your main MXML file has two essential elements:

**the header**: In the example above, the header tag `<?xml version="1.0" encoding="utf-8"?>` has two parts:

  - **XML declaration**: this tells the compiler what version of XML the file is using. 1.0 is the default; but since other versions exist, you have to specify it.
  - **The encoding**: this tells the compiler what text encoding to use to translate the bits of code into letters and numbers to display in the UI. The default is `utf-8`, but some applications use different encodings that suit their specific needs.
  
  
**The main tag**: This tag includes everything else on the page. For a full application, it usually starts `<js:Application...` and ends as the last line of the file: `</js:Application>`. In the component example above for a module that could be included in a larger application, the main tag defines a group: `<j:Group...` and closes at the end of the file: `</:Group>`.

The main tag's **attributes** are very important for configuring and launching the application. The attributes can include:

  - the app or component's name, which may appear in a header bar or in metadata the browser displays.
  - a declaration of **namespaces**. These are the location of resources you may want to use in the app. Declaring namespaces means you can deploy a control, container, or some other neat thing from that namespace without much struggle. In the component example above, because we declare the `xmlns:j="library://ns.apache.org/royale/jewel` in the main tag, we can later deploy buttons from that namespace (like `<j:Button text="Apache"/>`) very simply, using just "j" instead of the full URL of the namespace.
  - simple property values like the width and height of the app or module.
  - if the app or module implements or inherits from some other app or module.
  - what should happen as soon as the app is ready (something like `initialize="addEventListener('dataReady', dataReadyHandler);configurator.send()"`)

You write what this file does, how it does it, and what the user sees as a result, inside this main tag, after it opens and before its closing tag at the end of the file. See the "What your file _may_ have" section, below.

### What your file _should_ have ###

It is good to add, just under the XML declaration line, a **comments block** that includes a copyright statement, license notice, author notice, a statement of the purpose of the file, and other information useful for future file maintenance. The file will compile and run just fine without such a statement; but if you are building code others will see, try to maintain, and possibly want to reuse, you should include it.

### What your file _may_ have ###

A lot happens inside the main tag, and things can get complicated. The following elements to not all have to appear in every app or module, and do not have to appear in a specific order for the app to compile and run. But it's good to have a pattern you follow, especially if you are working as part of a team, so you can avoid wasting time trying to find something, forgetting to add something, or adding it twice.

**Declarations**: Define things like effects, validators, and formatters, and send and request data, inside the `<fx:Declarations>...</fx:Declarations>` tag.

**Metadata**: Add additional information to classes, properties, or methods to use at runtime inside the `<fx:Metadata>...</fx:Metadata>` tag. <a href="https://apache.github.io/royale-docs/features/as3/metadata">Learn more</a>.

**Functions, property definitions, and other features**: Declare properties, instantiate components, and write functions inside the `<fx:Script>...</fx:Script>` tag. In the component example above, we declare an _event handler_, a function that does things when you click one of the buttons in the user interface.



