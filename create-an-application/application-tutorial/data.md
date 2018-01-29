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

Since the goal of this application is to display a list of commits to the Royale GitHub repos, the data the application will work with must include that list of commits.  For large projects, the model is often built in a separate class and source file so it can be separately developed, documented, and maintained (maybe by other team members), but to get something up quickly, it can be easier to just stick a few variables in the main application file in a script block like this:

```
<fx:Script>
<![CDATA[
  public var commits:Array = [];
]]>
</fx:Script>
```

But thinking about this a bit more, it might be nice to not hard code which repos we use to get the commits so that other projects can use this app.  So let's add also:

```ActionScript
  public var repos:Array;
  public var projectName:String;
```

Next, we need to get the values for these arrays.  Let's use a .json file to configure which repos to use and the project name.  So create a file that looks like:

```JSON
{ "projectName": "Apache Royale",
  "repos":  [ "apache/royale-asjs", "apache/royale-typedefs", "apache/royale-compiler" ]
}
```
Now we need to add calls that fetch the .json file and then the commits.  We can use HTTPService to get the JSON file:

```XML
<js:HTTPService id="configurator" source="project.json" complete="setConfig();fetchCommits()" />
```
The method setConfig() sets the data model variables:

```ActionScript
private function setConfig():void
{
  repos = configurator.data.repos;
  projectName = configurator.data.projectName;
}
```

The method fetchCommits() will take the list of repos and calls a separate instance of HTTPServie to get the commits:

```XML
<js:HTTPService id="commitsService" />
```
```ActionScript
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
   commits = commits.concat(commitsService.data.commits);
   if (currentIndex < repos.length)
      fetchCommits();
}

```

Now if you build and run this, nothing will show up, so now let's go create the view (user interface).

{:align="center"}
[Previous Page](create-an-application/application-tutorial/main.html) \| [Next Page](create-an-application/application-tutorial/view.html)

