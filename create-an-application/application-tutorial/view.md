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

In an MVC application the View contains the user interface elements that display data and accept user input. We want a way to display the list of commits and also some useful information about those commits. In Royale a popular way to do that is with a DataGrid.

The main or initial view of an application is identified as its "initialView" property. We want our user interface elements to appear vertically so we use VView as the view:

```XML
<js:initialView>
  <js:VView>
  </js:VView>
</js:initialView>
```
Inside the VView tag we add the DataGrid

```XML
<js:DataGrid id="dg">
</js:DataGrid>
```

We want to display the date of the commit, who made the commit, and the commit message, each in their own column on each row of the DataGrid. So inside the DataGrid, we add:

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

Notice how the text of the label uses the projectName variable in the Model by wrapping the variable name in curly braces "{}".  In Royale, this is known as Data Binding. When the compiler sees curly braces in MXML attribute values, it generates code that sets the destination property (in this case, the Label's "text" property) to the value of the expression in the curly braces and also adds code that detects changes to that property and updates the destination property if the source value changes. This greatly reduces the amount of simple code you have to write. Without data binding, we'd probably hook up to an initialization event and also have to write:

```ActionScript
myLabel.text = projectName;
```

And we'd also have to write change detection code if the value could change at runtime (which it doesn't in this case). 

See more about what this powerful feature can do for you on this page: [Data binding](features/data-binding.html).

Also, a commit message might be too long to read in a row of a DataGrid so we will add a place to display the longer message of a selected commit.

<js:MultilineLabel text="{commits[dg.selectedIndex].message}" />

Notice how with data binding, we've written very little "code" to connect the DataGrid to the MultilineLabel.

We could use data binding to connect the commits array to the DataGrid, but it turns out the commits array is initialized to an empty array at startup and the commits variable is never assigned a different array so it never changes its value. Only the contents of the thing it references change. So data binding only detects changes in the expression, not changes to internal things referenced by the expression. 

It is possible to create something other than an Array that will dispatch change events so data binding will react, but due to the way the commits array is populated, that might result in updating the view for every commit, which isn't necessary (it might make a cool visual effect as rows appear, though). There are many other ways to hook up the commits array to the DataGrid, but for this case, we will listen for a dataReady event from the data model and assign the commits array then.  

In the script block we add a handler for the dataReady event.

```ActionScript
import org.apache.royale.collections.ArrayList;

private function dataReadyHandler(event:Event):void
{
    dg.dataProvider = new ArrayList(commits);
}

```
In the initialize handler, we add a listener for the dataReady event:

```ActionScript
addEventListener('dataReady', dataReadyHandler);
```

OK, so we've written the Model and now the View. On to the 'C' in MVC, the Controller.

{:align="center"}
[Previous Page](create-an-application/application-tutorial/data.html) \| [Next Page](create-an-application/application-tutorial/controller.html)
