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
title: The main application file
description: The file that serves as the entry point of your application
permalink: /create-an-application/application-tutorial/main
---

# The main application file

The file that serves as the entry point of your application

This application uses an [MXML](features/mxml) file as its main file.

The file starts with:

```mxml
<js:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
                xmlns:local="*"
                xmlns:js="library://ns.apache.org/royale/express" 
                >
```

The line:

```mxml
                xmlns:js="library://ns.apache.org/royale/express" 
```

means that the `js` prefix is mapped to the Express set of [components](user-interface/components.html). The Express set is designed for rapid prototyping and proofs-of-concepts and is not optimized for size and performance. Applications built with the Express components can still be deployed in production environments if the size and performance is acceptable, which it often is.

As mentioned in [Application structure](create-an-application/application-structure), there is more than one pattern for creating applications.  This example will use the [MVC pattern](https://en.wikipedia.org/wiki/Model–view–controller){:target='_blank'}.  So, the next step is to create the Model. 

{:align="center"}
[Previous Page](create-an-application/application-tutorial) \| [Next Page](create-an-application/application-tutorial/data-model)
