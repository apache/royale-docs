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
title: The data model
---

# The data model

Since the goal of this application is to display a list of commits to the Royale GitHub repositories (repos), the data the application will work with must include that list of commits. The application will query GitHub for the information, place what GitHub provides in a data structure, and then connect that data structure to components in the user interface that can display it.

For large projects, the model is often built in a separate class and source file so it can be separately developed, documented, and maintained (maybe by other team members). But to get something up quickly, we are going to just stick a few variables in the main application file in a script block.

First we create the data structure, in this case an array, to hold the information we get from GitHub:

```mxml
<fx:Script>
<![CDATA[
  public var commits:Array = [];
]]>
</fx:Script>
```

It might be nice to not hard-code which repos we use to get the commits so that other projects can use this app. So let's add variables to hold information about the project and repositories we are using:

```as3
  public var repos:Array;
  public var projectName:String;
```

Next, we need to get the values for these arrays. Let's use a <a href="https://www.json.org/" target="_blank">.json</a> file, called "project.json", to configure which repos to use and the project name. The file contents look like:

```json
{ "projectName": "Apache Royale",
  "repos":  [ "apache/royale-asjs", "apache/royale-typedefs", "apache/royale-compiler" ]
}
```
You can download this file from [here.](https://github.com/apache/royale-asjs/blob/develop/examples/express/GitHubCommitLogViewer/src/main/resources/project.json)

Now we need to add calls that fetch the .json file and then the information about the commits.  We can use HTTPService to get the JSON file:

```mxml
<js:HTTPService id="configurator" url="project.json" complete="setConfig();fetchCommits()" />
```
The method setConfig() sets the data model variables:

```as3
private function setConfig():void
{
  repos = configurator.json.repos;
  projectName = configurator.json.projectName;
}
```

The method fetchCommits() takes the list of repos and calls a separate instance of HTTPService to get information about the commits:

```mxml
<js:HTTPService id="commitsService" />
```

```as3
import org.apache.royale.events.Event;

private var currentIndex:int = 0;
private function fetchCommits():void
{
    commitsService.addEventListener("complete", gotCommits);
    commitsService.source = repos[currentIndex];
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

```

And, of course, we have to tell the service to go fetch the configuration file, so we add an "initialize" event handler to the Application tag to have the HTTPService send the request for the JSON file once the application is ready to receive the response.

```mxml
initialize="configurator.send()"
```

Now if you build and run this, nothing will show up. So now let's go create the view (user interface).

{:align="center"}
[Previous Page](create-an-application/application-tutorial/main.html) \| [Next Page](create-an-application/application-tutorial/view.html)

