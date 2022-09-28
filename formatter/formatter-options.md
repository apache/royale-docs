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

The [**asformat**](formatter) tool has a number of useful configuration options
. The list below is also available by running `asformat -help advanced` in a terminal.

- `-collapse-empty-blocks` -- Determines if empty blocks containing no statements will be collapsed to a single line, or if the closing curly brace should still appear on a new line.
- `-help` `[keyword]` `[...]` -- Displays formatter usage instructions.
- `-ignore-parsing-problems` -- If enabled, parsing errors will be ignored. This may result in undesirable effects on formatting.
- `-insert-final-new-line` -- Determines if the file must have at least one final new line.
- `-insert-space-anonymous-function-keyword` -- Determines if a space should appear between `function` and the opening parenthesis.
- `-insert-space-binary-operators` -- Determines if spaces should appear before and after binary operators, such as `+`, `==`, and `&&`.
- `-insert-space-comma-delimiter` -- Determines if a space should be inserted after a comma when used as a delimter (such as an object and array literals).
- `-insert-space-control-flow-keywords` -- Determines if a space should appear between control flow keywords, such as `if`, `for` and `while`, and the opening parenthesis.
- `-insert-space-for-loop-semicolon` -- Determines if a space should appear after each semicolon in a `for` loop.
- `-insert-space-line-comment` -- Determines if a single space should appear at the beginning of a line comment.
- `-insert-space-meta-attributes` -- Determines if a space should appear after metadata attributes.
- `-insert-spaces` -- Insert spaces for indentation.
- `-list-files` -- List files to standard output if they have formatting changes.
- `-load-config` `<filename>` -- Loads an XML configuration file with more formatter options.
- `-max-preserve-new-lines` `<int>` -- The maximum number of empty new lines to preserve between lines of code.
- `-mxml-align-attributes` -- When MXML attributes are on separate lines, align them at the start.
- `-mxml-insert-new-line-attributes` -- Determines if each MXML attribute should appear on a new line.
- `-open-brace-new-line` -- Determines if an opening curly brace should appear on a new line or not.
- `-semicolons` `<string>` -- Determines how to handle semicolons at the end of statements. Possible values are `ignore`, `insert`, or `remove`
- `-skip-local-config-file` -- Ignores _asformat-config.xml_ in the current working directory, if it exists.
- `-tab-size` `<int>` -- Sets the width of tab characters.
- `-version` -- Displays the version number of the formatter tool.
- `-write-files` -- Write changes to files that have been formatted.