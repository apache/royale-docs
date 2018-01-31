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
---

# Value Objects

Many servers return JSON which is just a plain object or array often referencing other plain objects and arrays.  In ActionScript there are advantages to using something called "data classes" or "value objects" (also sometimes "ValueObjects").

Value Objects tell the compiler that your data has a fixed set of properties of a given type.  If you misspell the name of a field in the data, the compiler will catch it.  Some IDEs know how to complete the field name as you type it and only offer completions for that data object instead of all strings used in the file.

And, they keep the Google Closure Compiler from renaming references to those fields, and allow you to have changes to the fields detected or ignored by the DataBinding code.

There is more than one way to create a Value Object for JSON objects.  This tutorial will use the simplest brute-force technique.  There are only three fields we are interested in out of the many fields and nested fields in the GitHub server response.  So instead of converting all of those fields or wrapping the JSON object and returning the nested fields, it is easier to just copy the three fields we need.

Many people prefer to keep their Value Objects in a folder/package.  For simplicity, we will just create the Value Object in the main "src" folder.  It will look like this:

```
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

Notice the use of [Bindable] metadata.  This special syntax indicaes to the compiler that there are no DataBinding notifications for the message field.   Once it is set, it will not change.  We could also specify "message" as a "const" instead of a "var" and set up a constructor with parameters, but constructor parameters are not allowed for anything that wants to be declared in MXML.

Once we have that, we use LogEntry throughout the app.  In the conversion loop, we change it to look like this:

```
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

And in the DataBinding to the MultilineLabel, we must also declare the type of the object in the Array so that the compilers know that the message property is from a LogEntry and should not be changed.

```
<js:MultilineLabel text="{LogEntry(commits[dg.selectedIndex]).message}" width="600" />
```

Compiling with these changes will eliminate the last warning that assignment to some variable cannot be detected since the [Bindable] metadata has instructed the compiler that the "message" property will not change at runtime.  But it still won't work.  That's because in the conversion loop, the JSON objects are also plain objects, and the Google Closure Compiler is going to rename expressions like obj.commit.author.name to things like "o.b.c.d".

Now we could define more Value Objects like LogEntry for these GitHub API data types, and if we do that, we should share it with everyone else (as of this writing we are seeking permission to do so), but given that we only have to tackle these JSON object in one place in the code and thus presents a good opporunity to show another technique to deal with renaming.

Another way to prevent the Google Closure Compiler from renaming variables is to use bracket notation.   In order to use the fewest number of bracket notations (because they are prone to mispelling) we will refactor the code a bit (which should also make it run a bit faster).  So the conversion loop will now look like this:

```
        for (var i:int = 0; i < n; i++)
        {
            var obj:Object = results[i];
            var data:LogEntry = new LogEntry();
            var commitObj:Object = obj["commit"];
            var authorObj:Object = commitObj["author"];
            data.author = authorObj["name"];
            // clip date after yyyy-mm-dd
            data.date = authorObj["date"].substr(0, 10);
            data.message = commitObj.message;
            commits.push(data);
        }
```

This should now work. And if you look in the js-release folder, you now have a single .js file to deploy (along with the .css, .json and .html file).  The .js.map file is there in case you have to debug this optimized .js file.  If you don't deploy it, anyone trying to reverse-engineer your application is in for quite a challenge!

If you weren't really following the steps and just skimming, the final result is available [here](create-an-application/application-tutorial/example/index.html){:target='_blank'}

This concludes the set of steps required to create a not-so-simple application and put it into production.  The next set of steps add additional features to the application.

{:align="center"}
[Previous Page](create-an-application/application-tutorial/production.html) \| [Next Page](create-an-application/application-tutorial/locales.html)
