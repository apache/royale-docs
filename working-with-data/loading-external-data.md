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
title: Loading External Data
description: Dynamic sites and real-time updates lead to good user experiences
permalink: /working-with-data/loading-external-data
---

# Loading External Data

Dynamic sites and real-time updates lead to good user experiences

Unless you are building a brochure-style website that makes a statement and provides contact information, you are going to be working with _data_. You will get some of that data from your site or application users, but you will probably also get a lot from outside your app or website.

Royale provides reliable, fast, and secure ways to get data from remote sources, and also to send data.

The following data types have built-in support:

* Raw Strings
* JSON
* [Binary](https://royale.apache.org/asdoc/#!org.apache.royale.utils/BinaryData)
* [XML](features/as3/xml)
* [AMF](working-with-data/loading-external-data/amf)

AMF is supported using either of:
* [LocalSharedObject](working-with-data/loading-external-data/localsharedobject)
* [RemoteObject](working-with-data/loading-external-data/remoteobject)

Classes which can be used for loading external data include:
* [HTTPService](working-with-data/loading-external-data/httpservice)
* [URLBinaryLoader](https://royale.apache.org/asdoc/#!org.apache.royale.net/URLBinaryLoader) for loading of any kind of binary data
* HttpRequestTask
* HttpDownloadTask

and others


