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
title: PAYG
---

# PAYG

PAYG stands for "pay as you go". The idea behind the concept is to keep component code as lightweight as possible, and to add functionality and complexity only to the components that need it. For example, you may use a lot of text input fields in your application, but only one or two need to be able to protect passwords by converting the display of text the user provides into dots. You may want to disable or enable some components, but not all of them, while an end user is working with your application. There is no reason to have that extra functionality (and added weight of code) available everywhere "just in case", as was the rule in Flex.

In Royale, you extend the basic functionality of a component with "beads" that you add to the "strand" of the component. Learn more about how to do this at [Strands and Beads](https://apache.github.io/royale-docs/Welcome/Features/Strands_and_Beads.html).
