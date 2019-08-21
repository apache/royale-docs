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
title: externs
---

# Externs

Some Apache Royale elements, like HTML dialog, at the moment have limited cross-browser support. To get reliable display and performance in those cases, Royale makes use of existing external JavaScript libraries.

Google Closure Compiler (GCC) provides a mechanism called @externs that is used in Apache Royale for declaring that a name is defined in external code and so should not be renamed.

The compiler assumes that externs will exist in the environment in which the compiled JavaScript will be interpreted.

So dialogPolyfill is an AS3 class with a line in the comments with @externs. That informs Apache Royale that this class is an extern for GCC. So that code already exists as a JS library and Apache Royale knows the methods a properties so you can get those in IDEs using code intelligence :)
