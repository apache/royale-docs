<!-- Writing conventions proposed by Andrew Wetmore, January 23, 2018 -->
# Apache Royale user documentation notes

## Audience
We have three main audiences:
1. Folks who have previously developed applications using Flex, and who want to learn whether and how to migrate their apps to Royale.
2. People who are new to AS and MXML, and possibly new to developing applications altogether, and want to know how to get started.
3. Experienced developers who want to see if Royale will give a better experience both in code development and through the application's lifecycle than what they have been using.

We can't assume that everybody understands the conversational shorthand Flex veterans use. Write for a person of good will who is reading to *find out*, and who wants to get to the next needed nugget of knowledge soon so they can go and make progress on the app they are working on. 

## Page structure
Each .md page starts with "front matter" structured like this:

```
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
title: README
---
```
Use HTML comments at the top of the document for any explanatory notes for the doc team (```<!-- Not finished yet - Andrew -->```) and for provenance when adapting existing material for Royale purposes (```<!-- Created by Peter Ent, modified by Tom Chiverton, as part of FlexJS documentation-->```).

## Documentation conventions
1. Address the reader directly, and in active voice, so "To do X, follow these steps..." rather than "When a developer wishes to do X, these steps would be followed..."
2. Instead of "he or she" use "they" when the pronoun is for an indefinite singular actor: "When someone has an existing application to migrate, they should start by..." This offends my grammarian soul, but is becoming standard English.
3. Link generously to other content in the help docs that may throw light on the current subject.
4. When writing how-to material, provide the *what*, the *so what*, and the *now what*: what a widget is, why widgets can be important in your code, and here's how to find, adapt, or create the widget of your dreams.

