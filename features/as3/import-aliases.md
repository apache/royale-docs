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
title: Import aliases
description: Import aliases in ActionScript
permalink: /features/as3/import-aliases
---

# Import aliases in ActionScript

-allow-import-aliases

[Apache Royale](https://royale.apache.org/){:target='_blank'} adds support for declaring _import aliaes_ in [ActionScript](features/as3). An import alias allows a class to be imported, but referenced in later code using a different base name. It is intended to help differentiate between multiple imported classes that have the same base name, but are in different packages, without having to use the fully-qualified name.

_Requires Apache Royale 0.9.6 or newer._

## Compiler option

Royale enables import aliases by default. To disable import aliases in your application, use the `-allow-import-aliases` compiler option.

```sh
mxmlc -allow-import-aliases=false MyApp.mxml
```

## Code example

Consider the following code that imports two classes named `Event`, but gives them aliases to differentiate between them:

```as3
package
{
    import ExampleEvent = com.example.events.Event;
    import RoyaleEvent = org.apache.royale.events.Event;

    public class MyClass
    {
        public function MyClass()
        {
            addEventListener(RoyaleEvent.CHANGE, onRoyaleEvent);
            addEventListener(ExampleEvent.EXAMPLE, onExampleEvent);
        }

        public function onRoyaleEvent(event:RoyaleEvent):void
        {

        }

        public function onExampleEvent(event:ExampleEvent):void
        {

        }
    }
}
```

## Limitations of import aliases in Royale

Other ActionScript compilers, such as the one in the [Apache Flex SDK](https://flex.apache.org/){:target='_blank'}, may not recognize import aliases. Attemping to pass ActionScript or MXML source code that contains import aliases to another compiler will result in compile-time errors. In other words, to write 100% portable ActionScript code that works with any compiler, avoid using abstract classes and any of Royale's other [extensions to the ActionScript language](features/as3#new-actionscript-language-features-in-royale).
