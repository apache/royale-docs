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
title: Testing
description: Methods for testing Apache Royale projects
permalink: /testing
---

# Testing with Apache Royale

Methods for testing Apache Royale projects

Every developer is building something from nothing, or adapting something that may already work into a new use, on a new platform, for a new audience. At every stage of the development process, there are more unknowns than knowns.

 - You may think you have written the code clearly and correctly, but when you compile it, it runs mysteriously slowly, or fails to run at all.
 - You proudly present the current state of the application to your stakeholders, and they shake their heads and say, "But that's not at all what we asked you to build."
 - Something that was working last week, or in the most recent build, is not working at all today.
 - Users are doing things with the app that you didn't expect them to do, like putting lines of code in a text entry field, and things are blowing up everywhere.

The main defense you have against buggy code and a failed development project is testing. Test early, test often...consider trying out [Test Driven Development](https://en.wikipedia.org/wiki/Test-driven_development){:target='_blank'}. 

Over time we will add pointers to general testing guides, and tips and tricks more specific to Apache Royale. Keep checking back, or consider contributing your own insights.

## Unit tests

Apache Royale includes the [RoyaleUnit](testing/royaleunit) library for unit testing.
