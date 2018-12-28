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
title: Strand and Beads
---

# Strand and Beads

__This material is not yet complete.__

Strands and beads are key concepts in Royale, related to the [PAYG](https://apache.github.io/royale-docs/Welcome/Features/PAYG.html)  (pay as you go) concept. The idea is to keep component code as lightweight as possible, and to add functionality and complexity only to the components that need it. For example, you may use a lot of text input fields in your application, but only one or two need to be able to protect passwords by converting the display of text the user provides into dots. There is no reason to have that extra functionality available everywhere "just in case", as was the rule in Flex.

Every component contains the minimum code necessary to perform its basic functions, with a "strand" onto which you can string "beads" of functionality that the component needs to do what you want it to do in a particular place in your application. 

## Finding the beads you need

_How to know what beads are available, and where they are_

## Adding a bead

_Steps for adding a bead_

## Creating a bead

_How to create a bead_

## Strand management

_Adding and removing beads; the significance of bead order_
