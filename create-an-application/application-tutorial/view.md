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
title: The view
---

# The view

In an MVC application the View contains the user interface elements that display data and accept user input.  For sure, we want a way to display the list of commits and also some useful information about those commits.  In Royale a popular way to do that is with a DataGrid.

The main or initial view of an application is assigned as the "initialView" property of the application.  We want our user interface elements to appear vertically so we will use VView as the view.  So, we add:

```XML
<js:initialView>
  <js:VView>
  </js:VView>
</js:initialView>
```
Then inside the VView tag we add the DataGrid

```XML
<js:DataGrid id="dg">
</js:DataGrid>
```

We want to display the date of the commit, who made the commit, and the commit message each in thir own column on each row of the DataGrid.  So inside the DataGrid, we add:

```XML
<js:columns>
  <js:DataGridColumn label="Date" dataField="date"/>
  <js:DataGridColumn label="Author" dataField="author"/>
  <js:DataGridColumn label="Message" dataField="message"/>
</js:columns>
```

Oh wait, we should have a label that displays the project name above the DataGrid, so before DataGrid add:

```XML
<js:Label text="{projectName} Commits Log"/>
```

Notice how the text of the label is referencing the projectName variable in the Model by wrapping the variable name in curly braces "{}".  In Royale, this is known as DataBinding.  When the compiler sees curly braces in MXML attribute values, it generates code that sets the destination property (in this case, the Label's "text" property) to the value of the expression in the curly braces and also adds code that detects changes to that property and updates the destination property if it changes.  This greatly reduces the amount of simple code you have to write yourself.  Otherwise, we'd probably hook up to an initialization event and have to also write:

```ActionScript
myLabel.text = projectName;
```

And we'd also have to write change detection code if the value could change at runtime, which it doesn't in this case.  To read more about DataBinding see this [section].

Also, a commit message might be too long to read in a row of a DataGrid so we will add a place to display the longer message of a selected commit.

<js:MultilineLabel text="{commits[dg.selectedIndex].message}" />

Notice how with DataBinding, we've written very little if any "code" to connect the DataGrid to the MultilineLabel.

We could use DataBinding to connect the commits array to the DataGrid, but it turns out the commits array is initialized to an empty array at startup and the commits variable is never assigned a different array so it never changes its value, only the contents of the thing it references change.  So DataBinding only detects changes in the expression, not changes to internal things referenced by the expression.  Now it is possible to create something other than an Array that will dispatch change events so DataBinding will react, but due to the way the commits array is populated, that might result in updating the view for every commit, which isn't necessary (might make a cool visual effect as rows appear though).  There are multiple other ways to implement a way to hook up the commits array to the DataGrid, but for this case, we will listen for a dataReady event from the data model and assign the commits array then.  In the script block we add a handler for the dataReady event.

```ActionScript
import org.apache.royale.collections.ArrayList;

private function dataReadyHandler(event:Event):void
{
    dg.dataProvider = new ArrayList(commits);
}

```
In the initialize handler, we add a listen for the dataReady event:

```ActionScript
addEventListener('dataReady', dataReadyHandler);
```

OK, so we've written the Model and now the View.  On to the 'C' in MVC, the Controller.

{:align="center"}
[Previous Page](create-an-application/application-tutorial/data.html) \| [Next Page](create-an-application/application-tutorial/controller.html)
