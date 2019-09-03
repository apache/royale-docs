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
description: Control access to application and the data
permalink: /create-an-application/application-tutorial/security
---

# Application security

Control access to application and the data

There are two sides to security:  

1. How do you access and get data or other material from an external source?
2. How do you keep certain external sites, processes or people from accessing your application and the things your application can access?

There is a separate section that deals with both topics in more detail, but the most common problem, especially for applications that mainly present data instead of collecting data, is how to access an external resource.

It is up the external resource to decide whether you can access it or not. And even if the external resource intends to let others access it, there may be rules and restrictions about who can get permission, and under what conditions. If you run into an access problem, look for documentation on "Cross-Origin Resource Sharing" or [CORS](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing){:target='_blank'}.

Fortunately, for this tutorial, GitHub's APIs are very permissive. Once you have your application on a website it should now show rows of commits even if it wasn't when running from `file://`.

{:align="center"}
[Previous Page](create-an-application/application-tutorial/debug) \| [Next Page](create-an-application/application-tutorial/production)
