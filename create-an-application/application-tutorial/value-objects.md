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
title: Value Objects
description: Plain ActionScript Objects with properties or arrays
permalink: /create-an-application/application-tutorial/value-objects
---

# Value Objects

Plain ActionScript Objects with properties or arrays

Queries for data to many servers return JSON, which is a plain object or array often referencing other plain objects and arrays. In ActionScript there are advantages to using something called "data classes" or "value objects" (also sometimes "ValueObjects").

Value Objects tell the compiler that your data has a fixed set of properties of a given type. If you misspell the name of a field in the data, the compiler will catch it. Some [IDEs](get-started/development-tools) know how to complete the field name as you type it and only offer completions for that data object instead of all strings used in the file.

Value Objects keep the [Google Closure Compiler (GCC)](https://developers.google.com/closure/compiler/){:target='_blank'} from renaming references to fields, and allow you to have changes to fields detected or ignored by the DataBinding code.

There is more than one way to create a Value Object for **JSON** objects. This tutorial will use the simplest, brute-force technique. There are only three fields we are interested in out of the many fields and nested fields in the GitHub server response. So instead of converting all fields or wrapping the JSON object and returning the nested fields, it is easier to just copy the three fields we need.

Many people prefer to keep their Value Objects in a separate folder/package. For simplicity in this tutorial, we will just create the Value Object in the main `src` folder. It will look like this:

```as3
package {
  public class LogEntry
  {
    public var date:String;
    public var author:String;

    [Bindable("__NoChangeEvent__")]
    public var message:String;
  }
}
```

You can download this file from [here](https://github.com/apache/royale-asjs/blob/develop/examples/express/GitHubCommitLogViewer/src/main/royale/LogEntry.as).

> Notice the use of [Bindable](features/data-binding) metadata with `__NoChangeEvent__`. This special syntax indicates to the compiler that there are no data binding notifications for the message field. Once it is set, it will not change. We could also specify `message` as a `const` instead of a `var` and set up a constructor with parameters, but constructor parameters are not allowed for anything that wants to be declared in MXML.

Once we have the `LogEntry` Value Object, we use `LogEntry` throughout the app. In the conversion loop, we change it to look like this:

```as3
  for (var i:int = 0; i < n; i++)
  {
      var obj:Object = results[i];
      var data:LogEntry = new LogEntry();
      data.author = obj.commit.author.name;
      // clip date after yyyy-mm-dd
      data.date = obj.commit.author.date.substr(0, 10);
      data.message = obj.commit.message;
      commits.push(data);
  }
```

In the data binding to the `MultilineLabel`, we must declare the type of the object in the Array so that the compilers know that the message property is from a `LogEntry` and should not be changed.

```mxml
<js:MultilineLabel text="{LogEntry(commits[dg.selectedIndex]).message}" width="600" />
```

Compiling with these changes will eliminate the warning that assignment to some variable cannot be detected, since the Bindable Metadata has instructed the compiler that the `message` property will not change at runtime. But we find it still won't work. That's because, in the conversion loop, the **JSON** objects are also plain objects, and the **GCC** is going to rename expressions like `obj.commit.author.name` to things like "o.b.c.d".

We could define more Value Objects like `LogEntry` for these GitHub API data types, and if we do that, we should share it with everyone else (as of this writing we are seeking permission to do so), but given that we only have to tackle these **JSON** object in one place in the code, this challenge presents a good opporunity to show another technique to deal with renaming.

> Another way to prevent the **GCC** from renaming variables is to use bracket notation. To use the fewest bracket notations (because they are prone to mispelling) we will refactor the code a bit (which should also make it run a bit faster). Now the conversion loop looks like this:

```as3
  for (var i:int = 0; i < n; i++)
  {
      var obj:Object = results[i];
      var data:LogEntry = new LogEntry();
      var commitObj:Object = obj["commit"];
      var authorObj:Object = commitObj["author"];
      data.author = authorObj["name"];
      // clip date after yyyy-mm-dd
      data.date = authorObj["date"].substr(0, 10);
      data.message = commitObj["message"];
      commits.push(data);
  }
```

This should now work. If you look in the `js-release` folder, you now have a single `.js` file to deploy (along with the `.css`, `.json` and `.html` files). The `.js.map` file is there in case you have to debug this optimized `.js` file. If you don't deploy it, anyone trying to reverse-engineer your application is in for quite a challenge!

If you weren't really following the steps and just skimming, the file in its final form is available [here](assets/application-tutorial/index.html){:target='_blank'}.

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" 
width="100%" height="350" 
src="assets/application-tutorial/index.html"></iframe>

This concludes the set of steps required to create a not-so-simple application and put it into production. The next steps, which are not yet complete, add additional features to the application.

{:align="center"}
[Previous Page](create-an-application/application-tutorial/production) \| [Next Page](create-an-application/application-tutorial/locales)
