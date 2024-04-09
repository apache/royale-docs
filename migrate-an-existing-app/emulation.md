---
# Licensed to the Apache Software Foundation (ASF) under one or more contributor license agreements.  See the NOTICE file distributed with this work for additional information regarding copyright ownership. The ASF licenses this file to You under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License.  You may obtain a copy of the License at
# 
# http://www.apache.org/licenses/LICENSE-2.0
# 
# Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

layout: docpage
title: Emulation
description: Create in Royale the Flex components you need
permalink: /migrate-an-existing-app/emulation
---

# Emulation

Create in Royale the Flex components you need

[Apache Royale](https://royale.apache.org/) offers a growing list of components that let you build your application and deploy it almost anywhere. However, there are still many features that were available in Adobe and Apache Flex and are "coming soon" in Royale. Most of these components relied on Flex APIs and either Adobe Flash or Adobe AIR, which a Royale application compiled into JavaScript and running on a browser cannot do.

Royale is creating a set of **emulation** components to replace the Flex components that depended on Flash features. These components do not promise 100% backward compatibility and may not use the same class hierarchy as Flex. But they do approximate what the equivalent components in Flex did.

There are two emulation [component sets](/component-sets):

* **MXRoyale** contains emulations of UIComponent and other MX components.
* **SparkRoyale** contains emulations of Spark components.

The Royale team typically discovers the need to emulate a component when a project or company starts to migrate an existing Flex application. We have developed guides to help developers create emulations that they need for their own applications, and that they can share with the community.

Further information is in these documents:

- [Creating a high-level emulation component](https://github.com/apache/royale-asjs/wiki/Creating-A-High-Level-Emulation-Component){:target="_blank"}

- [Emulation components](https://github.com/apache/royale-asjs/wiki/Emulation-Components){:target="_blank"}



