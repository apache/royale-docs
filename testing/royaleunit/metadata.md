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
title: Metadata
description: RoyaleUnit Metadata tags
permalink: /testing/royaleunit/metadata
---

# RoyaleUnit metadata

Metadata tags for defining unit tests with RoyaleUnit

The following ActionScript metadata tags may be used with RoyaleUnit test classes:

* [After](testing/royaleunit/metadata.html#after)
* [AfterClass](testing/royaleunit/metadata.html#afterclass)
* [Before](testing/royaleunit/metadata.html#before)
* [BeforeClass](testing/royaleunit/metadata.html#beforeclass)
* [Ignore](testing/royaleunit/metadata.html#ignore)
* [RunWith](testing/royaleunit/metadata.html#runwith)
* [Suite](testing/royaleunit/metadata.html#suite)
* [Test](testing/royaleunit/metadata.html#test)

## After

Specify a method to run after each test in this class.

## AfterClass

Specify a method to run one time, after all tests have completed in this class.

## Before

Specify a method to run before each test in this class.

## BeforeClass

Specify a method to run one time, before any tests have run in this class.

## Ignore

Specify that a specific test method should not run.

## RunWith

Specify the runner to be used with a specific test suite. Should be combined with [`[Suite]` metadata](testing/royaleunit/metadata.html#suite) metadata.

## Suite

Specify that a class is a test suite. Should be combined with Should be combined with [`[RunWith]` metadata](testing/royaleunit/metadata.html#runwith).

## Test

Specify that a method is a test that should be run.