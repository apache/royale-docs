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
title: Build the application
description: Building the application
permalink: /create-an-application/application-tutorial/build
---

# Build the application

Building the application

In many other *HTML/JS/CSS* development models, you write the *JS* and then just view it in the browser. [Apache Royale](https://royale.apache.org/) uses a compiler to convert your *MXML* and *ActionScript* code into *HTML/JS/CSS*. Why? Because there is a philosophy that the sooner you catch a bug, the less expensive it is to fix it. The compiler scans your source code to make sure that it makes sense. The compiler checks that there aren't typos in property names, that if you are expecting a `String` you'll probably get one, and more.  

The main *MXML* file should now look like this:

```mxml
<js:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
                xmlns:local="*"
                xmlns:js="library://ns.apache.org/royale/express"
                initialize="addEventListener('dataReady', dataReadyHandler);configurator.send()">
    <fx:Script>
    <![CDATA[
        import org.apache.royale.collections.ArrayList;
        import org.apache.royale.events.Event;

        public const commits:Array = [];
        public var repos:Array;
        public var projectName:String;

        private function setConfig():void
        {
            repos = configurator.json.repos;
            projectName = configurator.json.projectName;
        }

        private var currentIndex:int = 0;
        
        private function fetchCommits():void
        {
            commitsService.addEventListener("complete", gotCommits);
            commitsService.url = "https://api.github.com/repos/" + repos[currentIndex] + "/commits";
            commitsService.send();
        }

        private function gotCommits(event:Event):void
        {
            currentIndex++;
            var results:Array = commitsService.json as Array;
            var n:int = results.length;
            for (var i:int = 0; i < n; i++)
            {
                var obj:Object = results[i];
                var data:Object = {};
                data.author = obj.commit.author.name;
                // clip date after yyyy-mm-dd
                data.date = obj.commit.author.date.substr(0, 10);
                data.message = obj.commit.message;
                commits.push(data);
            }
            if (currentIndex < repos.length)
                fetchCommits();
            else
                dispatchEvent(new Event("dataReady"));
        }

        private function dataReadyHandler(event:Event):void
        {
            dg.dataProvider = new ArrayList(commits);
        }

    ]]>
    </fx:Script>
    
    <js:HTTPService id="configurator" url="project.json" complete="setConfig();fetchCommits()" />
    <js:HTTPService id="commitsService" />

    <js:initialView>
        <js:View>
            <js:Label text="{projectName} Commits Log"/>
            <js:DataGrid id="dg">
                <js:columns>
                    <js:DataGridColumn label="Date" dataField="date"/>
                    <js:DataGridColumn label="Author" dataField="author"/>
                    <js:DataGridColumn label="Message" dataField="message"/>
                </js:columns>
            </js:DataGrid>
            <js:Label text="Selected Message:"/>
            <js:MultilineLabel text="{commits[dg.selectedIndex].message}" />
        </js:View>
    </js:initialView>
</js:Application>
```

Before we compile this code, there are a few things we want to add. 

First, there is so far no way to know if a variable has changed. So we want to tell the compiler to convert the var into a get/set property so we can detect changes. Otherwise, you will get a warning that assignment to some variable cannot be detected. In Royale, this is done via [Metadata](features/as3/metadata). Metadata consists of square brackets `[]` which contain a tag and some attributes. The compiler knows to act on some MetaData. Other MetaData can be compiled into the code and used at runtime. To convert a var to a get/set property use the [Bindable] metadata. You can see it in the final code below.

Another thing missing is that we haven't specified the size of the controls. As with HTML/JS/CSS, there are several ways to do this. We could have a separate .css file, specify styles there and assign class names in the MXML tags. That allows the CSS to be tweaked without recompiling so you can just refresh the browser and see changes; but in Royale, the CSS file is actually generated by the compiler from the CSS file in your source code and CSS files in the libraries you used. So if you do make changes directly to the output CSS file, and want to keep the changes, you will need to make those changes in the source CSS file before compiling the source again.

This simple example will look fine if we just set the width and height of the DataGrid and the width of the MultilineLabel, so we will add them directly. You can read the section on Styles to see other ways of setting styles on the View.

The final code should look like this: (you can download it from [here](https://github.com/apache/royale-asjs/blob/develop/examples/express/GitHubCommitLogViewer/src/main/royale/GitHubCommitLogViewer.mxml).)

```mxml
<js:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
xmlns:local="*"
xmlns:js="library://ns.apache.org/royale/express"
initialize="addEventListener('dataReady', dataReadyHandler);configurator.send()"
>
<fx:Script>
<![CDATA[
    import org.apache.royale.collections.ArrayList;
    import org.apache.royale.events.Event;

    public const commits:Array = [];
    public var repos:Array;
    [Bindable]
    public var projectName:String;

    private function setConfig():void
    {
        repos = configurator.json.repos;
        projectName = configurator.json.projectName;
    }

    private var currentIndex:int = 0;
    
    private function fetchCommits():void
    {
        commitsService.addEventListener("complete", gotCommits);
        commitsService.url = "https://api.github.com/repos/" + repos[currentIndex] + "/commits";
        commitsService.send();
    }

    private function gotCommits(event:Event):void
    {
        currentIndex++;
        var results:Array = commitsService.json as Array;
        var n:int = results.length;
        for (var i:int = 0; i < n; i++)
        {
            var obj:Object = results[i];
            var data:Object = {};
            data.author = obj.commit.author.name;
            // clip date after yyyy-mm-dd
            data.date = obj.commit.author.date.substr(0, 10);
            data.message = obj.commit.message;
            commits.push(data);
        }
        if (currentIndex < repos.length)
            fetchCommits();
        else
            dispatchEvent(new Event("dataReady"));
    }

    private function dataReadyHandler(event:Event):void
    {
        dg.dataProvider = new ArrayList(commits);
    }

]]>
</fx:Script>
<js:HTTPService id="configurator" url="project.json" complete="setConfig();fetchCommits()" />
<js:HTTPService id="commitsService" />

<js:initialView>
    <js:VView>
        <js:Label text="{projectName} Commits Log"/>
        <js:DataGrid id="dg" width="600" height="300">
            <js:columns>
                <js:DataGridColumn label="Date" dataField="date" columnWidth="100"/>
                <js:DataGridColumn label="Author" dataField="author" columnWidth="100"/>
                <js:DataGridColumn label="Message" dataField="message" columnWidth="400"/>
            </js:columns>
        </js:DataGrid>
        <js:Label text="Selected Message:"/>
        <js:MultilineLabel text="{commits[dg.selectedIndex].message}" width="600" />
    </js:VView>
</js:initialView>
</js:Application>
```

Since we are interested in JS output, if you're using an [IDE](get-started/development-tools), set that output target in the project before compiling. If you're using command-line scripts, run:

`<path to Royale SDK>/royale-asjs/js/bin/mxmlc -debug=true GitHubCommitLogViewer.mxml`

If you've used [NPM](https://www.npmjs.com/){:target='_blank'} to install Royale, you can just run:

`mxmlc -debug=true GitHubCommitLogViewer.mxml`

This should compile with one warning. We will ignore that for now and fix it later.  Next, let's see the results.

{:align="center"}
[Previous Page](create-an-application/application-tutorial/controller) \| [Next Page](create-an-application/application-tutorial/deploy)
