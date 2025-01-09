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
title: Formatter Options
description: List of available formatter options
permalink: /formatter/formatter-options
---

# Formatter Options

List of all available formatter options

The [**asformat**](formatter) tool included with [Apache Royale](https://royale.apache.org/) has a number of useful configuration options
. The list below is also available by running `asformat -help advanced` in a terminal.

- `-collapse-empty-blocks` -- Determines if empty blocks containing no statements will be collapsed to a single line, or if the closing curly brace should still appear on a new line. Default: `false`
- `-help` `[keyword]` `[...]` -- Displays formatter usage instructions.
- `-ignore-parsing-problems` -- If enabled, parsing errors will be ignored. This may result in undesirable effects on formatting. Default: `false`
- `-insert-final-new-line` -- Determines if the file must have at least one final new line. Default: `false`
- `-insert-new-line-else` -- Determines if a new line is inserted before `else` when open braces are on new lines. Default: `true`
- `-insert-space-anonymous-function-keyword` -- Determines if a space should appear between `function` and the opening parenthesis. Default: `false`
- `-insert-space-binary-operators` -- Determines if spaces should appear before and after binary operators, such as `+`, `==`, and `&&`. Default: `true`
- `-insert-space-comma-delimiter` -- Determines if a space should be inserted after a comma when used as a delimter (such as an object and array literals). Default: `true`
- `-insert-space-control-flow-keywords` -- Determines if a space should appear between control flow keywords, such as `if`, `for` and `while`, and the opening parenthesis. Default: `true`
- `-insert-space-for-loop-semicolon` -- Determines if a space should appear after each semicolon in a `for` loop. Default: `true`
- `-insert-space-line-comment` -- Determines if a single space should appear at the beginning of a line comment. Default: `true`
- `-insert-space-meta-attributes` -- Determines if a space should appear after metadata attributes. Default: `true`
- `-insert-spaces` -- Insert spaces for indentation. Default: `false`
- `-list-files` -- List files to standard output if they have formatting changes. Default: `false`
- `-load-config` `<filename>` -- Loads an XML configuration file with more formatter options.
- `-max-preserve-new-lines` `<int>` -- The maximum number of empty new lines to preserve between lines of code. Default: `2`
- `-mxml-align-attributes` -- When MXML attributes are on separate lines, align them at the start. Default: `false`
- `-mxml-insert-new-line-attributes` -- Determines if each MXML attribute should appear on a new line. Default: `false`
- `-open-brace-new-line` -- Determines if an opening curly brace should appear on a new line or not. Default: `true`
- `-semicolons` `<string>` -- Determines how to handle semicolons at the end of statements. Supported values: `ignore`, `insert`, or `remove`. Default: `insert`
- `-skip-local-config-file` -- Ignores _asformat-config.xml_ in the current working directory, if it exists. Default: `false`
- `-tab-size` `<int>` -- Sets the width of tab characters. Default: `4`
- `-version` -- Displays the version number of the formatter tool.
- `-write-files` -- Write changes to files that have been formatted. Default: `false`