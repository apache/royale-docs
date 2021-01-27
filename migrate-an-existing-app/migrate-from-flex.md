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
description: Migrate an app from Flex to Royale
permalink: /migrate-an-existing-app/migrate-from-flex
---

<!-- This is from material created by Peter Ent and modified by Tom Chiverton: https://cwiki.apache.org/confluence/pages/viewpage.action?pageId=34013930 -->


# Migrate from Flex

New life for your Flex applications

If you have developed applications using the [Apache Flex SDK](https://flex.apache.org/){:target='_blank'}, or Adobe Flex before it, your applications probably combine [MXML](features/mxml) and [ActionScript](features/as3) files along with resources like images and audio files; and some of the MXML files have <fx:Script> tags with ActionScript snippets inside them. If that is the case, you will find yourself at home working with Apache Royale. The big difference is not so much the code you use, but the output and what it needs to run properly.

It is not yet possible to just import an existing Flex application into Apache Royale and then produce output in JavaScript that will run almost anywhere. However, you may need to do less hands-on conversion than you think to get to where you can use Royale to build your application, transpiled to JavaScript.

- ActionScript syntax is the same for Royale as it was in Flex. Functions, loops, classes, and properties will work as they worked before.
- Your "business logic", which you built in, or mainly in, ActionScript, probably does not need to change. 
- Components and their functions that do not rely on Apache Flex or Adobe Flash features will probably work with minor tweaks.

There are areas in your code base that will have to change. One is anywhere that uses **Flash APIs**. You can write a Flex application without importing and using any Flash classes, but most folks found it useful to call directly into Flash. Those calls have to change for most applications, as browsers no longer support Flash.

To determine where you may have used Flash APIs, look for "import flash" in your code. If you comment out all the "import flash" lines and re-compile, the compiler will show you every line that uses a Flash API.

Royale is creating a set of [emulation](/migrate-an-existing-app/emulation) components that deliver most, if not all, of the Flex APIs. These components do not promise 100% backward compatibility. Nor do they promise the same class hierarchy as Flex. They just try to approximate the functions their equivalents provided in Flex.

Some popular Flash APIs have been added to the Royale emulation of UIComponent, so review the documentation for UIComponent to see if it has a replacement for a Flash API your old app uses. If a replacement doesn't exist, it either hasn't been implemented yet in the emulation components or we have a good reason why it shouldn't be. Ask on the `users@royale.apache.org` mailing list if you want to know more about an emulation for a particular API.

Another category of changes is **namespaces**. In every MXML file you probably have one or both of:

```mxml
xmlns:s="library://ns.adobe.com/flex/spark" 
xmlns:mx="library://ns.adobe.com/flex/mx"

```

These need to change to:

```mxml
xmlns:s="library://ns.apache.org/royale/spark" 
xmlns:mx="library://ns.apache.org/royale/mx"

```

Making these changes will help us and you track what code is not using emulation components in MXML files.

Another category of changes is **API conflicts**. For example, in Flex, UIComponent (and thus all components and MXML files) had a 'document' property. The 'document' property conflicts with the 'document' object in the browser, so in the Royale emulation UIComponent we renamed 'document' to 'component'. Look for uses of 'document' and 'parentDocument' and change them to 'component' and 'parentComponent'.

Yet another category of changes is for **non-Flex SWCs**. If you used third-party libraries, you need to find Royale equivalents for them.  Royale is not developing emulations for any non-Apache Flex libraries at this time. Some third-party libraries may not have Flash dependencies and can just be transpiled with the Royale compiler. Others would take some effort to make Royale-compatible, and you may prefer to find a replacement SWC that Royale does support instead. Start a discussion on dev@royale.apache.org to find out what your options are.

## Running the compiler

The Royale compiler supports every option the Flex compiler supports. There are also some new options for controlling JavaScript output. Royale has an Ant task just as Flex does. It supports all the options that the Flex Ant task supports, plus some new options for controlling JavaScript output. You should be able to use the same options on the Royale compiler that you used when compiling your Flex app. The only thing you must add is the compiler option

`+configname=flex`

Then, assuming you aren't using any third-party libraries, your application should compile.

## Interpreting compiler errors and warnings

To start migrating your Flex app to Royale, try to get your code to compile without any "import flash' directives and use the Royale emulation components. You will get a bunch of errors and have to rename Flash APIs, and possibly comment out parts of the code that are not essential to getting the core of your application up and running. If you do that, use a special comment format so that, later, you can find places that are temporarily commented out and work on making them Royale-happy.

If you get errors about a component or API not found, it is likely that the emulations don't support that API yet. Ask on dev@royale.apache.org to find out what your options are. If you don't really have to use that API, comment it out for now.

You may see a warning about the use of "public var". As we mention in the tutorial, Royale uses a optimizing compiler for JavaScript output that renames variables to save on download size. That generally works fine unless the public vars represent fields in an object from an external source, like a JSON object or some other server result. You may need to change the public var to a getter and/or setter. Or you can suppress the warning by using the @royalesuppresspublicvarwarning directive.

You may see at the end of the compile output that says "namespace not provided yet". If you see that, ensure that the -remove-circulars compiler option is on. It should be on by default. If you still see that message, ask on the mailing list for assistance. More about circular dependencies can be found [here](migrate-an-existing-app/circular-dependencies.html)

## Running the migrated app after a successful compile

If you get a compile that has no errors, you can try running it. As mentioned in the tutorial, there is a debuggable version, bin/js-debug/index.html; and a production version, bin/js-release/index.html. Try the debuggable version first and check the JavaScript console output for errors.

If you use XML or Proxy in your application you will get lots of errors if you are not careful about strong typing. In your compiled Flex application, Flash knows the type of the instance and thus knows how to fetch a property for it. The Royale JavaScript runtimes don't know instance types, so as soon as your XML or Proxy instance is seen as a regular Object, things can go wrong. One place this is likely to happen is in ItemRenderers. They have a data property of type Object, so any code in the item renderer that looks like:

`data.property`

will not work if the data is XML or Proxy. Change this code so it is strongly-typed as, in the case of XML,

`(data as XML).property`

Once the debuggable version works, it is time to try the production version. If it doesn't work, check the JavaScript console for exceptions and errors and try to resolve them. Most errors, or just not getting the right results, will be due to variable renaming as described in the tutorial. Make sure you have resolved any public var warnings correctly. If you suppressed the warning but shouldn't have, that could cause a problem.

The production version is also likely to be more sensitive to a lack of strong typing. If an instance of a class gets thought of as a regular Object, the property might get renamed differently. Again, ItemRenderers are a common place this can happen.

In general, if something is not a plain Object, try to write your code so that the compiler knows it isn't an Object.
