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
title: High Level View
---
<!-- Based on material written by Peter Ent and modified by Tom Chiverton: https://cwiki.apache.org/confluence/pages/viewpage.action?pageId=34013930 -->

# High Level View

Apache Royale began as "FlexJS", a branch of the Apache Flex project. The goal was to make a way for the many existing Flex applications users have developed to be deployable outside of the Adobe Flash and Adobe AIR enviromments.

While Flex may work using Flash in browsers or within AIR on computers with traditional keyboards for years to come, Flex developers need to make their apps available on mobile devices, which for many end users are now the primary computer. The cost of migrating an application to a new coding language is high, and the risks around quality control are significant, especially when migrating to a less-strict language like JavaScript. Royale helps to minimize the cost and the risk of migration, while reusing much of the Flex code base without significant changes.

Beyond that, it is becoming clear that Royale can provide significant developer productivity gains for new projects. Flex made it easy and efficient to create robust applications. Like Flex, Royale provides:

- Declarative Language ([MXML](Welcome/Features/MXML.html)) - Declarative languages provide a schematic, or diagram. of the pieces of the application, and are more terse than options like JavaScript.
- Semi-Structured Language ([ActionScript](Welcome/Features/AS3.html)) - ActionScript deploys classes and interfaces, so it can do a better job of enforcing correct use of APIs than JavaScript can.
- Runtime Verifier - The verifier catches errors at runtime so you can address them before packaging a release.
- Choice of IDEs -  You can choose the IDE that suits you best, and the IDEs can provide better code assistance because the coding language is structured.

These features help you make fewer mistakes when writing code, and that saves time and improves productivity.

![How Royale fits together](_assets/as-mxmlsnapshot.png "MXML and AS working together")

<!-- Coming soon: LINK TO OM's UPDATED SLIDE SHOW http://events.linuxfoundation.org/sites/events/files/slides/FlexJS_ApacheCon_2015.pdf -->

## How it works
Because both [ActionScript](Welcome/Features/AS3.html) and JavaScript are based on the same language, ECMAScript, most code you write in AS translates well to JS. One significant difference is that AS uses the concepts of classes and objects to structure how your code functions, while pure JavaScript does not have those concepts. When you get ready to compile and run your application, the Royale compiler translates AS-specific code into JS code organized into pseudo-classes, which then run just fine in a JavaScript world.

That takes care of pretty much everything except the user interface. For that, Royale provides a set of UI containers and controls that do the work that the pure Flex containers and controls required the Flash engine to do.

## Status
Adobe Royale 0.9.1 was released in February, 2018. It is roughly of beta quality. The latest release is always available on the *Download* tab of this site.

Our project does not have a roadmap. As with most Apache projects, Royale is largely staffed by devoted volunteers. Rather than having a project owner who directs development, contributors come to agreement as a group about what they will work on next. Decisions are based on a combination of contributor skills and interests, and feature requests we receive from both Apache Flex and Royale users.

*Hint: the best way to move Royale forward is to join in and help!*


## Showcase
Visit "What Royale and you can do" to see examples, with source code, of what you can build with Apache Royale.
