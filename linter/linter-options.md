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
title: Linter Options
description: List of available linter options
permalink: /linter/linter-options
---

# Linter Options

List of all available linter options

The [**aslint**](linter) tool included with [Apache Royale](https://royale.apache.org/) has a number of useful configuration options. The list below is also available by running `aslint -help advanced` in a terminal.

- `-class-name` -- Ensures that class names match the pattern `^[A-Z][a-zA-Z0-9]*$`. Default: `false`
- `-constant-name` -- Ensures that constant names match the pattern `^[A-Z][A-Z0-9]*(_[A-Z0-9]+)*$`. Default: `false`
- `-empty-comment` -- Checks for comments that contain no text. Default: `false`
- `-empty-function-body` -- Checks for empty function bodies. Default: `false`
- `-empty-nested-block` -- Checks for empty blocks, except for bodies of classes, interfaces, and functions. Default: `false`
- `-empty-statement` -- Checks for statements that consist of only a semicolon. Default: `true`
- `-field-name` -- Ensures that field names match the pattern `^[_a-z][a-zA-Z0-9]*$`. Default: `false`
- `-function-name` -- Ensures that function names match the pattern `^[a-z][a-zA-Z0-9]*$`. Default: `false`
- `-help` `[keyword]` `[...]` -- Displays linter usage instructions.
- `-ignore-parsing-problems` -- If enabled, parsing errors will be ignored. This may result in undesirable effects. Default: `true`
- `-interface-name` -- Ensures that interface names match the pattern `^I[A-Z][a-zA-Z0-9]*$`. Default: `false`
- `-line-comment-position` `<string>` -- Requires single-line comments to appear at a specific position. Supported values: `above`, `beside` 
- `-load-config` `<filename>` -- Loads an XML configuration file with more linter options.
- `-local-var-param-name` -- Ensures that no local variables use the same name as one of the method's parameters. Default: `false`
- `-local-var-shadows-field` -- Ensures that no local variables use the same name as one of the class' fields. Default: `false`
- `-max-block-depth` `<int>` -- Checks that no nested blocks exceed a specific depth.
- `-max-params` `<int>` -- Ensures that no method has more than the specified number of parameters.
- `-missing-asdoc` -- Checks for missing or empty asdoc comments. Default: `false`
- `-missing-constructor-super` -- Checks for missing calls to `super()` in constructor. Default: `false`
- `-missing-namespace` -- Checks for missing namespaces on classes, interfaces, fields, and methods. Default: `false`
- `-missing-semicolon` -- Checks for missing semicolons. Default: `false`
- `-missing-type` -- Checks for missing variable types, method parameter types, and method return types. Default: `false`
- `-mxml-empty-attr` --  Checks for MXML attributes that contain no value. Default: `false`
- `-mxml-id` -- Ensures that MXML `id` values match the pattern `^[a-z][a-zA-Z0-9]*$`. Default: `false`
- `-no-any-type` -- Ensures that the `*` type is never used. Default: `false`
- `-no-boolean-equality` -- Checks for `==` or `!=` operators that redundantly compare to `true` or `false`. Default: `false`
- `-no-constructor-dispatch` -- Ensures that no events are dispatched from a constructor. Default: `false`
- `-no-constructor-return-type` -- Ensures that no return type is specified on a constructor. Default: `false`
- `-no-duplicate-keys` -- Checks for duplicate keys in object literals. Default: `true`
- `-no-dynamic-class` -- Ensurse that no class uses the `dynamic` modifier. Default: `false`
- `-no-if-boolean` -- Checks for `if (true)` or `if (false)`, which will always have the same result. Default: `true`
- `-no-leading-zero` -- Checks for numeric values with a leading `0`, which can be confused for octal notation. Default: `true`.
- `-no-sparse-array` -- Checks for empty slots in array literals, where there is no value between commas. Default: `true`.
- `-no-string-event` -- Ensures that strings are not passed to `addEventListener`, `removeEventListener`, or `hasEventListener`. Default: `false`
- `-no-this-closure` -- Ensures that the `this` keyword is not used inside closures. Default: `false`
- `-no-trace` -- Ensures that the code contains no `trace()` function calls. Default: `false`
- `-no-void-operator` -- Ensures that the `void` operator is never used. The `void` type is allowed. Default: `false`
- `-no-wildcard-import` -- Checks for imports that contain the `*` wildcard character. Default: `false`
- `-no-with` -- Ensures that the `with` keyword is never used. Default: `true`
- `-override-super` -- Checks for method overrides that contain only calls to the `super` method. Default: `false`
- `-package-name` -- Ensures that package names match the pattern `^[a-z][a-zA-Z0-9]*(\\.[a-z][a-zA-Z0-9]*)*$`. Default: `false`
- `-skip-local-config-file` -- Ignores _aslint-config.xml_ in the current working directory, if it exists. Default: `false`
- `-static-constants` -- Requires all constants on classes to have the `static` modifier. Default: `false`
- `-strict-equality` -- Ensures that comparisions use `===` or `!==` instead of `==` or `!=`. Default: `false`
- `-switch-default` -- Checks that all `switch` statements have a `default` case. Default: `false`
- `-unsafe-negation` -- Ensures that the `!` negation operator is used safely with `in`, `is`, and `instanceof`. Default: `true`
- `-valid-typeof` -- Checks the result of the `typeof` operator for invalid strings. Default: `true`
- `-vars-on-top` -- Requires all local variables to be declared at the top of a function. Default: `false`
- `-version` -- Displays the version number of the linter tool.