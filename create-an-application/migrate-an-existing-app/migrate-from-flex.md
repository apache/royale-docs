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
title: Migrate from Flex
---
<!-- This is from material created by Peter Ent and modified by Tom Chiverton: https://cwiki.apache.org/confluence/pages/viewpage.action?pageId=34013930 -->
# Migrate from Flex
If you have developed applications using <a href="http://flex.apache.org" target="_blank">Apache Flex</a>, or Adobe Flex before it, your applications probably combine MXML and ActionScript files along with resources like images and audio files, and some of the MXML files have <fx:Script> tags with ActionScript snippets inside them. If that is the case, you will find yourself at home working with Apache Royale. The big difference is not so much the code you use, but the output and what it needs to run properly.

It is not yet possible to just import an existing Flex application into Apache Royale and then produce output in JavaScript that will run almost anywhere. However, you may need to do less hands-on conversion than you think to get to where you can produce your application, transpiled to JavaScript, through Royale.

- ActionScript syntax is the same for Royale as it was in Flex. Functions, loops, classes, and properties will work as they worked before.
- Your "business logic", which you built all or mainly in ActionScript, probably does not need to change. 
- Components and their functions that do not rely on Apache Flex or Adobe Flash features will probably work with minor tweaks.

There are a few categories of changes to your code base.  One is where you used Flash APIs, if any.  In theory, you should have been able to write a Flex application without importing and using any Flash classes, but most folks found it useful to call directly into Flash.  Those calls will have to be changed.

To determine where you may have used Flash APIs look for "import flash" in your code.  If you comment out all of the "import flash" lines and re-compile, the compiler will show you every line that used a Flash API.

Royale is creating a set of "emulation" components that will eventually have most, if not all, of the Flex APIs.  These components do not promise 100% backward compatibility.  Nor do they promise the same class hierarchy as Flex.  They just try to approximate what Flex did.

Some popular Flash APIs have been added to the Royale emulation of UIComponent, so look for at the documentation for UIComponent for a replacement for Flash API usage.  If it doesn't exist, then it either hasn't been implemented yet in the emulation components or we have a good reason why.  Ask on the users@royale.apache.org mailing list if unsure.

Another category of changes is namespaces.  In every MXML file you probably have one or both of:

```
xmlns:s="library://ns.adobe.com/flex/spark" 
xmlns:mx="library://ns.adobe.com/flex/mx"

```

These will need to be changed to:

```
xmlns:s="library://ns.apache.org/royale/spark" 
xmlns:mx="library://ns.apache.org/royale/mx"

```

We may not have had to force you to make these changes, but we think it will help us and you track what code is not using emulation components in MXML files.


Another category of changes is API conflicts.  For example, in Flex, UIComponent (and thus all components and MXML files) had a 'document' property.  The 'document' property conflicts with the 'document' object in the browser, so in the Royale emulation, UIComponent had 'document' renamed to be 'component'.  You will want to look for uses of 'document' and 'parentDocument' and change them to be 'component' and 'parentComponent'.

Yet another category of changes is for non-Flex SWCs.  If you used third-party libraries, you will need to find Royale equivalents for them.   Royale is not developing any emulations for any non-Apache Flex libraries at this time.  Some third-party libraries may not have Flash dependencies and can just be transpiled with the Royale compiler.  Others will take some effort and you may prefer to find a different SWC that Royale does support instead.  Start a discussion on dev@royale.apache.org to find out what your options are.

## Running the compiler

The Royale compiler supports every options the Flex compiler supports.  In addition there are some new options for controlling JavaScript output.  Royale also has an Ant task just like Flex does.  It supports all of the options that the Flex Ant task supports, plus some new options for controlling JavaScript output.  You should be able to use the same compiler options on the Royale compiler as you did when compiling your Flex app.  The only thing you must add is the compiler option

```
+configname=flex
```

THen, assuming you aren't using any third-party libraries, your application should compile.


## Intepreting Compiler Errors and Warnings

The migration process is probably best done by first trying to get your code to compile without any "import flash' directives and using the Royale emulation components.  You will get a bunch of errors and have to rename Flash APIs, and possibly comment out other parts that are not essential to getting the application up and running.  We recommend that you use a special comment format so you can find places that are temporarily commented out.

If you get errors about a component or API not found, then it is likely that the Emulation doesn't support that API yet.  Ask on dev@royale.apache.org to find out what your options are.  If you don't really have to use that API, comment it out for now.

You may see an warning about the use of "public var".  As described in the tutorial, Royale uses a optimizing compiler for JavaScript output that will rename variables in order to save on download size.  That generally works fine unless the public vars represent fields in an object from an external source like a JSON object or other server result.  You may need to change the public var to a getter and/or setter.  Or, you can suppress the warning by using the @royalesuppresspublicvarwarning directive.

You may see at the end of the compile output that says "namespace not provided yet".  If you see that, ensure that the -remove-circulars compiler option is on.  It should be on by default.  If you still see that, ask on the mailing list for assistance.  More about circular dependencies can be found [here](create-an-application/migrate-an-existing-app/circular-dependencies.html)

## Running the migrated app after a successful compile

If you get a compile that has no errors, you can try running it.  As mentioned in the tutorial, there is a debuggable version in bin/js-debug/index.html, and a production version in bin/js-release/index.html.  First try the debuggable version and check JavaScript console output for errors.

If you use XML or Proxy in your application you will get lots of errors if you are not careful about strong typing.  Unlike in Flash, where Flash knows the type and thus knows how to fetch a property of the instance, the JavaScript runtimes don't, so as soon as your XML or Proxy instance is seen as a regular Object, things can go wrong.  One place this is likely to happen is in ItemRenderers.  They have a data property of type Object.  So any code in the item renderer that looks like:

```
data.property
```

will not work if data is XML or Proxy.  This code as to be strongly-typed as, in the case of XML,

```
(data as XML).property
```

Once the debuggable version works, it is time to try the production version.  If it doesn't work, first check the JavaScript console for exceptions and errors and try to resolve those.  Most errors, or just not getting the right results will be due to variable renaming as described in the tutorial.  Make sure you have resolved any public var warnings correctly.  If you suppressed the warning but shouldn't have, that could cause a problem.

The production version is also likely to be more sensitive to lack of strong typing.  If you have an instance of a class, if the instance gets thought of as a regular Object, the property might get renamed differently.  Again, ItemRenderers are a common place this can happen.

In general, if something is not a plain Object, try to write your code so that the compiler knows it isn't an Object.
