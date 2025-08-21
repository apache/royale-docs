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
title: aslint-config.xml
description: Configure aslint with an external aslint-config.xml file
permalink: /linter/aslint-config-file
---

# _aslint-config.xml_

Configure the Royale linter for a specific project

If the current working directory contains an _aslint-config.xml_ file, the [**aslint**](linter) tool included with [Apache Royale](https://royale.apache.org/) will conveniently load this file automatically to configure its options.

The root of this file is an `<aslint-config>` element. To specify a [linter option](linter/linter-options), add it as a child element.

```xml
<aslint-config>
    <max-params>5</max-params>
    <no-dynamic-class>true</no-dynamic-class>
    <line-comment-position>beside</line-comment-position>
</aslint-config>
```

For boolean option values, set the text inside the opening and closing tags to `true` or `false`. For numeric option values, use the digits 0-9. For string option values, enter the text as you would on the command line.

## Disable _aslint-config.xml_

To disable loading the _aslint-config.xml_ file, use the `-skip-local-config-file` option.

```sh
aslint --skip-local-config-file src/com/example/MyClass.as
```