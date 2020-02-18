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
title: Module support
description: Module support in Crux
permalink: /libraries/crux/module-support
---

# Module support

Learn about module support in Crux

## Parent and Child Crux Instances

Crux supports the concept of parent and child instances. Typically, this capability is used in conjunction with Modules. When you load a module that contains a Crux instance as a child of another Crux-based application, the framework will create a parent-child relationship between these two instances of Crux. This happens automatically, meaning that the developer should not have to do any manual setup or configuration to use this feature.
<!-- There is a sample application that demonstrates how Crux can work with Modules at the Github repository. -->