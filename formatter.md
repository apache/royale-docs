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
title: Formatter
description: Using the Royale formatter with ActionScript and MXML
permalink: /formatter
---

# Apache Royale Formatter

Format your _.as_ and _.mxml_ source files

## User Guide

Below are some pointers to help you get started with the [Apache Royale](https://royale.apache.org/) formatter in various environments.

### Command line

The _bin_ directory of the Royale SDK should contain the **asformat** script that will launch the formatter. Use `asformat --help` to see a [list of available formatter options](formatter/formatter-options).

To use the default formatting options, simply pass in the path to a _.as_ or _.mxml_ file as an argument.

```sh
asformat src/com/example/MyClass.as
```

The formatted file contents will be printed to the standard output only, and the original file will remain unmodified. To save the formatting changes, use the `--write-files` option (or its shorter `-w` alias).

```sh
asformat --write-files src/com/example/MyClass.as
```

To format multiple files, pass in a directory path. The formatter will search this directory recursively for _.as_ and _.mxml_ files, and it will format every one that it finds.

```sh
asformat --write-files src
```

To see which files were changed by the formatter, use the `--list-files` option (or its shorter `-l` alias).

```sh
asformat --write-files --list-files src
```

### Editors and IDEs

Consult your editor or IDE documentation to see whether it integrates the Royale formatter or not. Many development environments have the ability to run external command line programs, even if the Royale formatter is not directly integrated.

## Formatter configuration

The Royale formatter provides a number of command line options to customize its use. You can also save a list of the options for your project in a local configuration file that will be detected automatically.

- [List of formatter options](formatter/formatter-options)
- [_asformat-config.xml_](formatter/asformat-config-file)
