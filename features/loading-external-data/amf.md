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
description: ActionScript Message Format
permalink: /features/loading-external-data/amf
---

# AMF

ActionScript Message Format

AMF is a great way to send data between an Apache Royale client and a backend server. The server could be written in Java, PHP, .NET, Ruby, Python and many other backend technologies.

[Action Message Format (AMF)](https://en.wikipedia.org/wiki/Action_Message_Format){:target='_blank'} is a binary format used to serialize object graphs such as ActionScript objects and XML, or send messages between a client and a remote service. The Actionscript 3 language provides classes for encoding and decoding from the AMF format, also backend servers need to know how to encode and decode AMF.

Since 2018, Apache Royale is capable to encode/decode AMF3 for all AS3 data types with the exception of flash Dictionary and Vector classes that we expect will be implemented in the future. AMF0 is not supported at this time. Some Applications are currently in production using the Apache Royale implementation.

## Language back-end servers supporting AMF

Here's a list of languages backend that supports AMF that can work with Apache Royale. Only a few has been tested with Apache Royale at this time:

| Server            | Library Name                                                                          | Royale Tested     | 
|------------------	|---------------------------------------------------------------------------------- 	|-----------------  | 
| **Java**          | [Apache Flex BlazeDS](https://github.com/apache/flex-blazeds){:target='_blank'}	    | **YES**           | 
| **.NET**          | [FluorineFX](https://github.com/google-code-export/fluorinefx){:target='_blank'}	    | **YES**           | 
| **PHP** 	        | [AMFPHP](https://www.silexlabs.org/amfphp){:target='_blank'}                  	    | **YES**           | 
| **Python** 	    | [AMFFast](https://github.com/limscoder/amfast){:target='_blank'}	                    | NO                | 
| **Perl** 	        | [AMF::Perl](https://metacpan.org/pod/AMF::Perl){:target='_blank'}	                    | NO                | 
| **Ruby**          | [RubyAMF](https://github.com/rubyamf/rubyamf){:target='_blank'}	                    | NO                | 
| **ColdFusion**    | [Coldfusion](https://www.adobe.com/products/coldfusion/features){:target='_blank'}	| NO                | 

> if you are working with some of the listed languages and can provide information about the working state of the library or want to notify about another new working implementation please let us know in our user or dev [mailing lists](https://royale.apache.org/mailing-lists/).

## How to use AMF format in Apache Royale

Apache Royale supports AMF protocol through the following implementations:

- [RemoteObject](features/loading-external-data/remoteobject)
- [LocalSharedObject](features/loading-external-data/localsharedobject)

