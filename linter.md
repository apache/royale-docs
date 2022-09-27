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
title: Linter
description: Using the Royale linter with ActionScript and MXML
permalink: /linter
---

# Apache Royale Linter

Discover common issues in your _.as_ and _.mxml_ source files

## User Guide

Below are some pointers to help you get started with the Royale linter in various environments.

### Command line

The _bin_ directory of the Royale SDK should contain the **aslint** script that will launch the linter. Use `aslint --help` to see a [list of available linter options](linter/linter-options).

To use the default linting options, simply pass in the path to a _.as_ or _.mxml_ file as an argument.

```sh
aslint src/com/example/MyClass.as
```

To lint multiple files, pass in a directory path. The linter will search this directory recursively for _.as_ and _.mxml_ files, and it will lint every one that it finds.

```sh
aslint src
```

### Editors and IDEs

Consult your editor or IDE documentation to see whether it integrates the Royale linter or not. Many development environments have the ability to run external command line programs, even if the Royale linter is not directly integrated.

## Linter configuration

The Royale linter provides a number of command line options to customize its use. You can also save a list of the options for your project in a local configuration file that will be detected automatically.

- [List of linter options](linter/linter-options)
- [_aslint-config.xml_](linter/aslint-config-file)
