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
title: Release build file size optimization
description: How to reduce the size of release builds
permalink: /compiler/release-build-file-size-optimization
---
# Release build file size optimization

Reduce the size of release builds

A number of [compiler options](compiler/compiler-options) are available for [Apache Royale](https://royale.apache.org/) that allow you to reduce the output size of JavaScript release builds. However, using these options may also prevent certain coding patterns in ActionScript and JavaScript (such as reflection capabilities) from working correctly, so read carefully to understand what the tradeoffs are for enabling these options and whether it will affect how you must write your code.

There are two main ways to reduce the size of a release build:

- Disabling exported symbols to external JavaScript
- Allowing symbols to be renamed as part of minification

A symbol, in this case, is a class, an interface, a field, or a method. It is possible to control these settings based on a symbol's namespace, such as `public`, `protected`, or `internal`. Symbols that are `private` are never exported and may be renamed.

> These options are available when compiling a release build of an _application_ with the **mxmlc** compiler. They are not supported when compiling a _library_ with the **compc** compiler. Libraries are always compiled as debug builds when targeting JavaScript, and they will be optimized later, if they are included in an application's release build.

## Disable exported symbols

If a symbol is _exported_, it may be accessed by external JavaScript `<script>` elements in the same page. If a symbol is not exported, and it is not referenced elsewhere in the Royale project, the compiler may determine that it is "dead code" that should be removed from a release build.

If external JavaScript never needs to access variables or call functions exposed by your Royale application, it should be safe to disable export of symbols.

The following options are available to control whether symbols are exported or not. Symbols that are `private` are never exported.

- [`-export-public-symbols`](compiler/compiler-options#export-public-symbols)
- [`-export-protected-symbols`](compiler/compiler-options#export-protected-symbols)
- [`-export-internal-symbols`](compiler/compiler-options#export-internal-symbols)

## Allow renaming of symbols

When you prevent the compiler from renaming a symbol in a minifinied release build, the symbol may be accessed using dynamic string access, such as `object["myProperty"]`. If a symbol is allowed to be renamed, the compiler may determine that it can change the name of the symbol to a shorter value to reduce the size of the release build. If a symbol is renamed, dynamic string access will not be possible without knowing the new name of the symbol.

The following [compiler options](compiler/compiler-options) are available to control whether symbols may be renamed or not, based on the namespace.

- [`-prevent-rename-public-symbols`](compiler/compiler-options#prevent-rename-public-symbols)
- [`-prevent-rename-protected-symbols`](compiler/compiler-options#prevent-rename-protected-symbols)
- [`-prevent-rename-internal-symbols`](compiler/compiler-options#prevent-rename-internal-symbols)

Additionally, several more granular [compiler options](compiler/compiler-options) are available to prevent or allow certain _categories_ of symbols to be renamed.

- [`prevent-rename-public-static-methods`](compiler/compiler-options.html#prevent-rename-public-static-methods)
- [`prevent-rename-public-instance-methods`](compiler/compiler-options.html#prevent-rename-public-instance-methods)
- [`prevent-rename-public-static-variables`](compiler/compiler-options.html#prevent-rename-public-static-variables)
- [`prevent-rename-public-instance-variables`](compiler/compiler-options.html#prevent-rename-public-instance-variables)
- [`prevent-rename-public-static-accessors`](compiler/compiler-options.html#prevent-rename-public-static-accessors)
- [`prevent-rename-public-instance-accessors`](compiler/compiler-options.html#prevent-rename-public-instance-accessors)
- [`prevent-rename-protected-static-methods`](compiler/compiler-options.html#prevent-rename-protected-static-methods)
- [`prevent-rename-protected-instance-methods`](compiler/compiler-options.html#prevent-rename-protected-instance-methods)
- [`prevent-rename-protected-static-variables`](compiler/compiler-options.html#prevent-rename-protected-static-variables)
- [`prevent-rename-protected-instance-variables`](compiler/compiler-options.html#prevent-rename-protected-instance-variables)
- [`prevent-rename-protected-static-accessors`](compiler/compiler-options.html#prevent-rename-protected-static-accessors)
- [`prevent-rename-protected-instance-accessors`](compiler/compiler-options.html#prevent-rename-protected-instance-accessors)
- [`prevent-rename-internal-static-methods`](compiler/compiler-options.html#prevent-rename-internal-static-methods)
- [`prevent-rename-internal-instance-methods`](compiler/compiler-options.html#prevent-rename-internal-instance-methods)
- [`prevent-rename-internal-static-variables`](compiler/compiler-options.html#prevent-rename-internal-static-variables)
- [`prevent-rename-internal-instance-variables`](compiler/compiler-options.html#prevent-rename-internal-instance-variables)
- [`prevent-rename-internal-static-accessors`](compiler/compiler-options.html#prevent-rename-internal-static-accessors)
- [`prevent-rename-internal-instance-accessors`](compiler/compiler-options.html#prevent-rename-internal-instance-accessors)