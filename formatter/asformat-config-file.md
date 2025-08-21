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
title: asformat-config.xml
description: Configure asformat with an external asformat-config.xml file
permalink: /formatter/asformat-config-file
---

# _asformat-config.xml_

Configure the Royale formatter for a specific project

If the current working directory contains an _asformat-config.xml_ file, the [**asformat**](formatter) tool included with [Apache Royale](https://royale.apache.org/) will conveniently load this file automatically to configure its options.

The root of this file is an `<asformat-config>` element. To specify a [formatter option](formatter/formatter-options), add it as a child element.

```xml
<asformat-config>
    <collapse-empty-blocks>true</collapse-empty-blocks>
    <max-preserve-new-lines>3</max-preserve-new-lines>
    <semicolons>ignore</semicolons>
</asformat-config>
```

For boolean option values, set the text inside the opening and closing tags to `true` or `false`. For numeric option values, use the digits 0-9. For string option values, enter the text as you would on the command line.

## Disable _asformat-config.xml_

To disable loading the _asformat-config.xml_ file, use the `-skip-local-config-file` option.

```sh
asformat --skip-local-config-file --write-files src/com/example/MyClass.as
```