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
title: Application security
---

# Application security

There are two sides to security:  How do you access something external resource?  And, How do you keep certain external resources from accessing your application and the things your application can access.  There is a separate section that deals with both topics in more detail, but the most common problem, especially for applications that mainly present data instead of collect data, is how to access an external resource.

It is up the external resource to decide whether you can access it or not.  And even if the external resource intends to let others access it, there may be rules and restrictions in order to get permission.  If you run into an access problem, look for documentation on "Cross-Origin Resource Sharing" or "CORS".

Fortunately, for this tutorial, GitHub's APIs are very permissive and the application should now show rows of commits if it wasn't when running from file://.

{:align="center"}
[Previous Page](create-an-application/application-tutorial/debug.html) \| [Next Page](create-an-application/application-tutorial/production.html)
