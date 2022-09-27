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

The [**aslint**](linter/) tool has a number of useful configuration options. The list below is also available by running `aslint -help advanced` in a terminal.

- `-class-name` -- Ensures that class names follow a certain pattern.
- `-constant-name` -- Ensures that constant names follow a certain pattern.
- `-empty-comment` -- Checks for comments that contain no text.
- `-empty-function-body` -- Checks for empty function bodies.
- `-empty-nested-block` -- Checks for empty blocks, except for bodies of classes, interfaces, and functions.
- `-empty-statement` -- Checks for statements that consist of only a semicolon.
- `-field-name` -- Ensures that field names follow a certain pattern.
- `-function-name` -- Ensures that function names follow a certain pattern.
- `-help` `[keyword]` `[...]` -- Displays linter usage instructions.
- `-ignore-parsing-problems` -- If enabled, parsing errors will be ignored. This may result in undesirable effects.
- `-interface-name` -- Ensures that interface names follow a certain pattern.
- `-line-comment-position` `<string>` -- Requires single-line comments to appear at a specific position.
- `-load-config` `<filename>` -- Loads an XML configuration file with more linter options.
- `-local-var-param-name` -- Ensures that no local variables use the same name as one of the method's parameters.
- `-local-var-shadows-field` -- Ensures that no local variables use the same name as one of the class' fields.
- `-max-block-depth` `<int>` -- Checks that no nested blocks exceed a specific depth.
- `-max-params` `<int>` -- Ensures that no method has more than the specified number of parameters.
- `-missing-asdoc` -- Checks for missing or empty asdoc comments.
- `-missing-constructor-super` -- Checks for missing calls to `super()` in constructor.
- `-missing-namespace` -- Checks for missing namespaces on classes, interfaces, fields, and methods.
- `-missing-semicolon` -- Checks for missing semicolons.
- `-missing-type` -- Checks for missing variable types, method parameter types, and method return types.
- `-mxml-empty-attr` --  Checks for MXML attributes that contain no value.
- `-mxml-id` -- Ensures that MXML `id` values follow a certain pattern.
- `-no-any-type` -- Ensures that the `*` type is never used.
- `-no-boolean-equality` -- Checks for `==` or `!=` operators that redundantly compare to `true` or `false`.
- `-no-constructor-dispatch` -- Ensures that no events are dispatched from a constructor.
- `-no-constructor-return-type` -- Ensures that no return type is specified on a constructor.
- `-no-duplicate-keys` -- Checks for duplicate keys in object literals.
- `-no-dynamic-class` -- Ensurse that no class uses the `dynamic` modifier.
- `-no-if-boolean` -- Checks for `if (true)` or `if (false)`, which will always have the same result.
- `-no-leading-zero` -- Checks for numeric values with a leading `0`, which can be confused for octal notation.
- `-no-sparse-array` -- Checks for empty slots in array literals, where there is no value between commas.
- `-no-string-event` -- Ensures that strings are not passed to `addEventListener`, `removeEventListener`, or `hasEventListener`.
- `-no-this-closure` -- Ensures that the `this` keyword is not used inside closures.
- `-no-trace` -- Ensures that the code contains no `trace()` function calls.
- `-no-void-operator` -- Ensures that the `void` operator is never used. The `void` type is allowed.
- `-no-wildcard-import` -- Checks for imports that contain the `*` wildcard character.
- `-no-with` -- Ensures that the `with` keyword is never used.
- `-override-super` -- Checks for method overrides that contain only calls to the `super` method.
- `-package-name` -- Ensures that package names follow a certain pattern.
- `-skip-local-config-file` -- Ignores _aslint-config.xml_ in the current working directory, if it exists.
- `-static-constants` -- Requires all constants on classes to have the `static` modifier.
- `-strict-equality` -- Ensures that comparisions use `===` or `!==` instead of `==` or `!=`.
- `-switch-default` -- Checks that all `switch` statements have a `default` case.
- `-unsafe-negation` -- Ensures that the `!` negation operator is used safely with `in`, `is`, and `instanceof`.
- `-valid-typeof` -- Checks the result of the `typeof` operator for invalid strings.
- `-vars-on-top` -- Requires all local variables to be declared at the top of a function.
- `-version` -- Displays the version number of the linter tool.