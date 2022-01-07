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
title: XML
description: XML in ActionScript 3
permalink: /features/as3/xml
---

# XML

XML in ActionScript 3

## XML: A first class citizen
ActionScript has support for XML as a native type.

## Some history
In 2004 and 2005, [Ecma published ECMA-357](https://www.ecma-international.org/publications-and-standards/standards/ecma-357/) which was a spec for handling XML in Javascript. The spec was called E4X (Ecmascript for XML). This was adopted by Firefox (SpiderMonkey) and ActionScript. Unfortunately [it was not adopted by Chrome](https://bugs.chromium.org/p/v8/issues/detail?id=235), so it never became a Javascript standard.

Today, E4X lives on in ActionScript, Adobe's ExtendScript and [Rhino Javascript](http://mozilla.github.io/rhino/).

## Types
The XML spec defines 4 additonal types
- Namespace -- which has a uri and a prefix
- QName -- a qualified name which can reference a local name to either a prefix or uri
- XML -- A native type which holds the XML. XML nodes can be elements, attributes, text, etc.
- XMLList --  A special XML-like type which holds a list of XML objects. If the XMLList contains a single child, it can be used as if it is XML.

XML and XMLList has special properties so they can be used as if they are text (when they are text nodes).

## E4X
The goal of E4X is to give an intuitive interface to read, traverse and filter XML.
### Operators
E4X adds three basic operators. The dot (`.`) operator in E4X means "child" and the `.@` operator means "attribute". The `..` operator means descendent. So you can get all children with the name `child` by using `root.child` or an attribute by using `root.child.@name` `root..child` will return all descendents named "child" no matter how far down the hierarchy they are.

### Filtering
E4X also allows filtering. Let's say you want to get only child who's name is "Bob". You can do that by using `root.(child.@name == "Bob)`. To help grasp the syntax, you can think of `.()` as a "filter function". The above expression in English would be "give me all children of root whose name attribute equals Bob". As you can see, the syntax is very concise, intuitive and quite powerful.

## Limitations
Because XML and E4X is not supported natively by the browser, some E4X code needs to be rewritten by the compiler. For this to work, the compiler needs to know that an object is XML. For this reason it's very important to be consistent about declaring XML types in Royale. Particular care should be taken if you have an array of XML objects to either use `Vector`, declare a local variable (i.e. `var item:XML = arr[i]`) or use function access instead of E4X syntax. To further clarify: `myUnknownXML.child("foo")` will work as expected, but `myUnknownXML.foo` will not.

## Optimization
We have done a lot of work to make XML and E4X as performant as possible. It's being used in production of applications with a lot of XML data without issues. However the E4X spec can sometimes lend itself to code which creates a lot of extra work for the Javascript engine.

It's also possible to end up in situations where large amounts of XML are stored in memory. If there's a reference to a single XML node anywhere, the entire tree cannot be garbage collected.

For these cases, the browser profiling tools are your friend.

### Use with caution
For the first issue, use the profiler to see if XML processing is taking measurable time. If yes, you can optimize your code by using two methods we added to XML in Royale: `getChildrenArray()` and `getAttributeArray()`. Use these methods with care and *only* use them if you need to optimize your code. These will return the underlying list of children and attributes respectively. Please note that this returns the *actual* arrays and *not* a copy. The reason they don't return copies is to allow modification without creating XMLLists from the data. In performance sensitive situations, accessing the underlying structures can give measurable benefits.

For the second issue, make sure to use `copy()` if you need to keep specific XML nodes around. Or you can save the serialized XML as a string and rewrite it as XML later. You can use the memory profiling tools to see if there's excessive XML usage.
## Alternative
Full XML and E4X support does carry with it some performance implications. Royale also offers a lightweight [JXON](https://royale.apache.org/asdoc/#!org.apache.royale.utils/JXON) class which can be useful for simple reading of XML.

Some limitations of the JXON implementation are:
- No E4X
- No writing of XML. It's for consuming XML only.
- No namespace support
- Doesn't handle whitespace

## Where to go from here
- MDN had very good documentation of E4X. Unfortunately it has been removed. It's still viewable using [WayBackMachine](http://web.archive.org/web/20160304033553/https://developer.mozilla.org/en-US/docs/Archive/Web/E4X_tutorial/Introduction).
- StackOverflow has [lots of good information on E4X](https://stackoverflow.com/questions/tagged/e4x).
- Web articles. There are various articles on E4X scattered around the web. The content is sure to be old, but relevant.