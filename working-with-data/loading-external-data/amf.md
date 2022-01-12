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
title: AMF
description: ActionScript Message Format binary protocol
permalink: /working-with-data/loading-external-data/amf
---

# AMF

ActionScript Message Format binary protocol

AMF is a great way to send data between an Apache Royale client and a backend server. The server could be written in Java, PHP, ColdFusion, .NET, Ruby, Python or many other backend technologies.

[Action Message Format (AMF)](https://en.wikipedia.org/wiki/Action_Message_Format){:target='_blank'} is a binary format used to serialize object graphs such as ActionScript objects and XML, or send messages between a client and a remote service. The ActionScript 3 language provides classes for encoding and decoding from the AMF format. Backend servers need to know how to encode and decode AMF.

Since 2018, Apache Royale has been able to encode/decode AMF3 for all AS3 data types with the exception of Flash Dictionary and Vector classes. We expect to implement those data types in the future. Royale does not support AMF0 at this time. Some applications are currently in production using the Apache Royale AMF implementation.

## Language back-end servers supporting AMF

Here's a list of languages used to create backend servers that support AMF and can, in theory, work with Apache Royale. We have only tested a few of the servers with Apache Royale so far, and welcome learning of developers' experiences.

| Server            | Library Name                                                                          | Royale Tested     | 
|------------------	|---------------------------------------------------------------------------------- 	|-----------------  | 
| **Java**          | [Apache Flex BlazeDS](https://github.com/apache/flex-blazeds){:target='_blank'}	    | **YES**           | 
| **.NET**          | [FluorineFX](https://github.com/google-code-export/fluorinefx){:target='_blank'}	    | **YES**           | 
| **PHP** 	        | [AMFPHP](https://www.silexlabs.org/amfphp){:target='_blank'}                  	    | **YES**           | 
| **Python** 	    | [AMFFast](https://github.com/limscoder/amfast){:target='_blank'}	                    | NO                | 
| **Perl** 	        | [AMF::Perl](https://metacpan.org/pod/AMF::Perl){:target='_blank'}	                    | NO                | 
| **Ruby**          | [RubyAMF](https://github.com/rubyamf/rubyamf){:target='_blank'}	                    | NO                | 
| **ColdFusion**    | [Coldfusion](https://www.adobe.com/products/coldfusion/features){:target='_blank'}	| NO                | 

> if you are working with any of the listed languages and can provide information about the working state of the library, or want to report other back-end implementations that work with AMF, please let us know in our user or dev [mailing lists](https://royale.apache.org/mailing-lists/).

## How to use AMF format in Apache Royale

Apache Royale supports the AMF protocol through these implementations:

- [RemoteObject](working-with-data/loading-external-data/remoteobject)
- [LocalSharedObject](working-with-data/loading-external-data/localsharedobject)

