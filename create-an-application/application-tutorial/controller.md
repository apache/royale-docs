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
title: The controller
description: Watching events from the View and updating the Model
permalink: /create-an-application/application-tutorial/controller
---

# The controller

Watching events from the View and updating the Model

The controller is the code that watches for events from the View and updates the Model. Why separate that out? Because that way a View can be reused in other applications. Our View right now is pretty generic and could be used to display comments on a wiki page, or a text messaging conversation, or even some social media discussion.

Right now, the View's only interaction (other than scrolling through the list of commits) is selecting a commit so you can see any longer commit message in the `MultilineLabel`. That doesn't really update the model, so this application's controller currently has nothing to do. Also, the most of the individual components like `DataGrid` are themselves implemented in the [MVC](https://en.wikipedia.org/wiki/Model–view–controller){:target='_blank'} pattern and the `DataGrid` has a controller that handles selection and updating the `selectdItem` property. But when we add localization and filters later, the controller will start to get busy. 

If there were a reason to share the currently selected commit with other Views, the Model could be extended to have a `currentCommit` field and then the controller would watch for `DataGrid` selection changes and update the model.

So, nothing to do here for now. Let's try to compile and run our application.

{:align="center"}
[Previous Page](create-an-application/application-tutorial/view) \| [Next Page](create-an-application/application-tutorial/build)
