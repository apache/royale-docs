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
title: Compiler Options
description: List of available compiler options
permalink: /compiler/compiler-options
---

# Compiler Options

List of available compiler options

## Contents

**General compiler options**
* [allow-abstract-classes](compiler/compiler-options.html#allow-abstract-classes)
* [allow-private-constructors](compiler/compiler-options.html#allow-abstract-constructors)
* [allow-import-aliases](compiler/compiler-options.html#allow-import-aliases)
* [strict-identifier-names](compiler/compiler-options.html#strict-identifier-names)

**JavaScript compiler options**
* [html-output-filename](compiler/compiler-options.html#html-output-filename)
* [html-template](compiler/compiler-options.html#html-template)
* [js-compiler-option](compiler/compiler-options.html#js-compiler-option)
* [js-default-initializers](compiler/compiler-options.html#js-default-initializers)
* [js-dynamic-access-unknown-members](compiler/compiler-options.html#js-dynamic-access-unknown-members)
* [js-define](compiler/compiler-options.html#js-define)
* [js-load-config](compiler/compiler-options.html#js-load-config)
* [js-output](compiler/compiler-options.html#js-output)
* [js-vector-emulation-class](compiler/compiler-options.html#js-vector-emulation-class)
* [jsx-factory](compiler/compiler-options.html#jsx-factory)
* [remove-circulars](compiler/compiler-options.html#remove-circulars)
* [source-map](compiler/compiler-options.html#source-map)
* [source-map-source-root](compiler/compiler-options.html#source-map-source-root)
* [targets](compiler/compiler-options.html#targets)
* [warn-public-vars](compiler/compiler-options.html#warn-public-vars)
* [show-binding-warnings](compiler/compiler-options.html#show-binding-warnings)

**Reduce output size**
You can use these options to reduce the size of your compiled application:

* [export-public-symbols](compiler/compiler-options.html#export-public-symbols)
* [export-protected-symbols](compiler/compiler-options.html#export-protected-symbols)
* [export-internal-symbols](compiler/compiler-options.html#export-internal-symbols)
* [prevent-rename-public-symbols](compiler/compiler-options.html#prevent-rename-public-symbols)
    * [prevent-rename-public-static-methods](compiler/compiler-options.html#prevent-rename-public-static-methods)
    * [prevent-rename-public-instance-methods](compiler/compiler-options.html#prevent-rename-public-instance-methods)
    * [prevent-rename-public-static-variables](compiler/compiler-options.html#prevent-rename-public-static-variables)
    * [prevent-rename-public-instance-variables](compiler/compiler-options.html#prevent-rename-public-instance-variables)
    * [prevent-rename-public-static-accessors](compiler/compiler-options.html#prevent-rename-public-static-accessors)
    * [prevent-rename-public-instance-accessors](compiler/compiler-options.html#prevent-rename-public-instance-accessors)
* [prevent-rename-protected-symbols](compiler/compiler-options.html#prevent-rename-protected-symbols)
    * [prevent-rename-protected-static-methods](compiler/compiler-options.html#prevent-rename-protected-static-methods)
    * [prevent-rename-protected-instance-methods](compiler/compiler-options.html#prevent-rename-protected-instance-methods)
    * [prevent-rename-protected-static-variables](compiler/compiler-options.html#prevent-rename-protected-static-variables)
    * [prevent-rename-protected-instance-variables](compiler/compiler-options.html#prevent-rename-protected-instance-variables)
    * [prevent-rename-protected-static-accessors](compiler/compiler-options.html#prevent-rename-protected-static-accessors)
    * [prevent-rename-protected-instance-accessors](compiler/compiler-options.html#prevent-rename-protected-instance-accessors)
* [prevent-rename-internal-symbols](compiler/compiler-options.html#prevent-rename-internal-symbols)
    * [prevent-rename-internal-static-methods](compiler/compiler-options.html#prevent-rename-internal-static-methods)
    * [prevent-rename-internal-instance-methods](compiler/compiler-options.html#prevent-rename-internal-instance-methods)
    * [prevent-rename-internal-static-variables](compiler/compiler-options.html#prevent-rename-internal-static-variables)
    * [prevent-rename-internal-instance-variables](compiler/compiler-options.html#prevent-rename-internal-instance-variables)
    * [prevent-rename-internal-static-accessors](compiler/compiler-options.html#prevent-rename-internal-static-accessors)
    * [prevent-rename-internal-instance-accessors](compiler/compiler-options.html#prevent-rename-internal-instance-accessors)

## General compiler options

### allow-abstract-classes {#allow-abstract-classes}

Determines if the `abstract` modifier may be used with classes. For more details, see [Abstract Classes in ActionScript](features/actionscript/abstract-classes.html).

```sh
-compiler.allow-abstract-classes
```

### allow-private-constructors {#allow-private-constructors}

Determines if the `private` namespace may be used with class constructors. For more details, see [Private Constructors in ActionScript](features/actionscript/private-constructors.html).

```sh
-compiler.allow-private-constructors
```

### allow-import-aliases {#allow-import-aliases}

Determines if alias syntax for for imported symbols is allowed or not.

```sh
-compiler.allow-import-aliases
```

### strict-identifier-names {#strict-identifier-names}

Determines if names of identifiers must follow the strict rules of ActionScript 3.0, or if they may use the looser rules introduced in ECMAScript 5. Defaults to `false`.

```sh
-compiler.strict-identifier-names
```

## JavaScript compiler options

### html-output-filename {#html-output-filename}

Specifies the file name of the HTML file generated by the compiler to load the Apache Royale application in the browser.

```sh
-compiler.html-output-filename custom.html
```

### html-template {#html-template}

Specifies the path to an optional template for the HTML file generated by the compiler to load the Apache Royale application in the browser.

```sh
-compiler.html-template ./path/to/template.html
```

#### Maven configuration:

```xml
<htmlTemplate>${basedir}/target/javascript/bin/js-debug/jewel-example-index-template.html</htmlTemplate>
```

### js-compiler-option {#js-compiler-option}

Specifies one or more custom compiler options to pass to the Google Closure Compiler, which is used to create the release build of an Apache Royale application.

```sh
-compiler.js-compiler-option.variable_map_output_file gccvars.txt -compiler.compilation_level SIMPLE_OPTIMIZATIONS
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-js-compiler-option=--variable_map_output_file gccvars.txt;-js-compiler-option+=--property_map_output_file gccprops.txt</additionalCompilerOptions>
```

### js-default-initializers {#js-default-initializers}

Defaults to true. Enables or disables initialization of primitive (Number, Boolean, etc.) variables with default values in the generated JavaScript. Corresponds to AVM runtime implicit type intialization values.

Note that some reflection utility functions require this to be set to true in order for them to work correctly in JavaScript.  

```sh
-compiler.js-default-initializers
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-js-default-initializers=true;</additionalCompilerOptions>
```

### js-dynamic-access-unknown-members {#js-dynamic-access-unknown-members}

If the definition of a member cannot be resolved at compile time, emit dynamic access instead of normal member access. Ensures that dynamic members aren't renamed.

```sh
-compiler.js-dynamic-access-unknown-members 
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-js-dynamic-access-unknown-members=true;</additionalCompilerOptions>
```

### js-define {#js-define}

Defines a global constant at compile time for the JavaScript output. May be a boolean, number, string, or expression.

```sh
-compiler.js-define CONFIG::debugging true -compiler.js-define CONFIG::release false
```

For Boolean and numeric values, you may pass in literals like true, false, or 123. Format string values with nested quotes, like "'hello'", because the compiler will attempt to evaluate an expression when it encounters a quotation mark.

#### Maven configuration:

```xml
<defines>
    <property>
        <name>BUILD::buildNumber</name>
        <value>'"${buildTimestamp}"'</value>
    </property>
    <property>
        <name>BUILD::buildVersion</name>
        <value>'"${project.version}"'</value>
    </property>
</defines>
```

Then in AS3 you can do:

```as3
// Build Number
private static var _buildNumber :String = BUILD::buildNumber;

// Project Version
private static var _projectVersion :String = BUILD::buildVersion;
```

### js-load-config {#js-load-config}

Specifies the locations of XML configuration files that define extra compiler options for JavaScript output.

```sh
-compiler.js-load-config path/to/project-config.xml
```

#### Maven configuration:

### js-output {#js-output}

The path where the generated JavaScript output should be saved, if your are also using it for the .swf output path.

```sh
-compiler.js-output path/to/output
```

#### Maven configuration:

Use instead `outputDirectory`in `configuration` xml node

### js-vector-emulation-class {#js-vector-emulation-class}

A custom implemention to use instead of default emulation of the AVM2 `Vector` typed collection.

```sh
-compiler.js-vector-emulation-class=com.example.MyVectorClass
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-js-vector-emulation-class=com.example.MyVectorClass;</additionalCompilerOptions>
```

### jsx-factory {#jsx-factory}

Customize the factory to use for JSX syntax. Defaults to `React.createElement`.

```sh
-compiler.jsx-factory=_jsx
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-jsx-factory=_jsx;</additionalCompilerOptions>
```

### remove-circulars {#remove-circulars}

Tells the Apache Royale compiler to remove circular dependencies in the generated JavaScript, where possible.

```sh
-compiler.remove-circulars
```

#### Maven configuration:

```xml
<removeCirculars>true</removeCirculars>
```

### source-map {#source-map}

Emits a source map in the debug build for each ActionScript file. The default value is false.

```sh
-compiler.source-map
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-source-map=true;</additionalCompilerOptions>
```

### source-map-source-root {#source-map-source-root}

Sets a custom value for the `sourceRoot` property in the generated source map files. This option will be ignored if the `source-map` compiler option is `false`.

```sh
-compiler.source-map-source-root=my/custom/path
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-source-map-source-root=my/custom/path;</additionalCompilerOptions>
```

### targets {#targets}

Specifies the target format of the code generated by the Apache Royale compiler. You can specify multiple targets.

```sh
-compiler.targets JSRoyale,SWF
```

The compiler supports the following values for "targets":

- "JSRoyale"
- "JS"
- "JSNode"
- "JSNodeModule"
- "SWF"

#### Maven configuration:

```xml
<targets>JSRoyale</targets>
```

### warn-public-vars {#warn-public-vars}

Enables or disables warnings about using public variables when it may be considered dangerous to use them.

```sh
-compiler.warn-public-vars
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-warn-public-vars=true;</additionalCompilerOptions>
```

### show-binding-warnings {#show-binding-warnings}

Set to false to remove all binding warnings.

```sh
-compiler.show-binding-warnings=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-show-binding-warnings=false;</additionalCompilerOptions>
```


## Reduce size of release builds

The following compiler options may be used to reduce the output size of JavaScript release builds. However, using these options may also prevent certain coding patterns in ActionScript and JavaScript from working correctly, so use with caution.

There are two main ways to reduce the size of a release build:

- **Disable exported symbols.**  When a symbol is _exported_, it may be accessed by external JavaScript `<script>` elements in the same page. If a symbol is not exported, and it is not referenced elsewhere in the Royale project, the compiler may determine that it is "dead code" that should be removed from a release build.

- **Allow renaming of symbols.** When a symbol is not allowed to be renamed in a release build, it may be accessed using dynamic string access, such as `object["myProperty"]`. If a symbol is not prevented from being renamed, the compiler may determine that it can change the name of the symbol to a shorter value to reduce the size of the release build. If a symbol is renamed, dynamic string access will not be possible without knowing the new name of the symbol.

### Export public symbols {#export-public-symbols}

In a release build, determines if symbols in the `public` namespace will be exported or not. The default value is `true`.

```sh
-export-public-symbols=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-export-public-symbols=false;</additionalCompilerOptions>
```

### Export protected symbols {#export-protected-symbols}

In a release build, determines if symbols in the `protected` namespace will be exported. The default value is `false`.

```sh
-export-protected-symbols=true
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-export-protected-symbols=true;</additionalCompilerOptions>
```

### Export internal symbols {#export-internal-symbols}

In a release build, determines if symbols in the `internal` namespace will be exported. The default value is `false`.

```sh
-export-internal-symbols=true
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-export-internal-symbols=true;</additionalCompilerOptions>
```

### Prevent renaming of public symbols {#prevent-rename-public-symbols}

In a release build, determines if symbols in the `public` namespace may be renamed or not. The default value is `true`.

```sh
-prevent-rename-public-symbols=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-public-symbols=false;</additionalCompilerOptions>
```

#### Related options:

When `prevent-rename-public-symbols` option is `true`, one or more the following options may be set to `false` to allow renaming of certain specific subsets of public symbols.

- [`prevent-rename-public-static-methods`](compiler/compiler-options.html#prevent-rename-public-static-methods)
- [`prevent-rename-public-instance-methods`](compiler/compiler-options.html#prevent-rename-public-instance-methods)
- [`prevent-rename-public-static-variables`](compiler/compiler-options.html#prevent-rename-public-static-variables)
- [`prevent-rename-public-instance-variables`](compiler/compiler-options.html#prevent-rename-public-instance-variables)
- [`prevent-rename-public-static-accessors`](compiler/compiler-options.html#prevent-rename-public-static-accessors)
- [`prevent-rename-public-instance-accessors`](compiler/compiler-options.html#prevent-rename-public-instance-accessors)

### Prevent renaming of protected symbols {#prevent-rename-protected-symbols}

In a release build, determines if symbols in the `protected` namespace may be renamed or not. The default value is `true`.

```sh
-prevent-rename-protected-symbols=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-protected-symbols=false;</additionalCompilerOptions>
```

#### Related options:

When `prevent-rename-protected-symbols` option is `true`, one or more the following options may be set to `false` to allow renaming of certain specific subsets of protected symbols.

- [`prevent-rename-protected-static-methods`](compiler/compiler-options.html#prevent-rename-protected-static-methods)
- [`prevent-rename-protected-instance-methods`](compiler/compiler-options.html#prevent-rename-protected-instance-methods)
- [`prevent-rename-protected-static-variables`](compiler/compiler-options.html#prevent-rename-protected-static-variables)
- [`prevent-rename-protected-instance-variables`](compiler/compiler-options.html#prevent-rename-protected-instance-variables)
- [`prevent-rename-protected-static-accessors`](compiler/compiler-options.html#prevent-rename-protected-static-accessors)
- [`prevent-rename-protected-instance-accessors`](compiler/compiler-options.html#prevent-rename-protected-instance-accessors)

### Prevent renaming of internal symbols {#prevent-rename-internal-symbols}

In a release build, determines if symbols in the `internal` namespace may be renamed or not. The default value is `true`.

```sh
-prevent-rename-internal-symbols=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-internal-symbols=false;</additionalCompilerOptions>
```

#### Related options:

When `prevent-rename-internal-symbols` option is `true`, one or more the following options may be set to `false` to allow renaming of certain specific subsets of internal symbols.

- [`prevent-rename-internal-static-methods`](compiler/compiler-options.html#prevent-rename-internal-static-methods)
- [`prevent-rename-internal-instance-methods`](compiler/compiler-options.html#prevent-rename-internal-instance-methods)
- [`prevent-rename-internal-static-variables`](compiler/compiler-options.html#prevent-rename-internal-static-variables)
- [`prevent-rename-internal-instance-variables`](compiler/compiler-options.html#prevent-rename-internal-instance-variables)
- [`prevent-rename-internal-static-accessors`](compiler/compiler-options.html#prevent-rename-internal-static-accessors)
- [`prevent-rename-internal-instance-accessors`](compiler/compiler-options.html#prevent-rename-internal-instance-accessors)

### Prevent renaming of public static methods {#prevent-rename-public-static-methods}

In a release build, determines if static methods in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-static-methods=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-methods=false;</additionalCompilerOptions>
```

### Prevent renaming of public instance methods {#prevent-rename-public-instance-methods}

In a release build, determines if instance (non-static) methods in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-instance-methods=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-public-instance-methods=false;</additionalCompilerOptions>
```

### Prevent renaming of public static variables {#prevent-rename-public-static-variables}

In a release build, determines if static variables in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-static-variables=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-variables=false;</additionalCompilerOptions>
```

### Prevent renaming of public instance variables {#prevent-rename-public-instance-variables}

In a release build, determines if instance (non-static) variables in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-instance-variables=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-public-instance-variables=false;</additionalCompilerOptions>
```

### Prevent renaming of public static accessors {#prevent-rename-public-static-accessors}

In a release build, determines if static accessors (getters and setters) in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-static-accessors=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-accessors=false;</additionalCompilerOptions>
```

### Prevent renaming of public instance accessors {#prevent-rename-public-instance-accessors}

In a release build, determines if instance (non-static) accessors (getters and setters) in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-instance-accessors=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-public-instance-accessors=false;</additionalCompilerOptions>
```

### Prevent renaming of protected static methods {#prevent-rename-protected-static-methods}

In a release build, determines if static methods in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-static-methods=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-methods=false;</additionalCompilerOptions>
```

### Prevent renaming of protected instance methods {#prevent-rename-protected-instance-methods}

In a release build, determines if instance (non-static) methods in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-instance-methods=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-protected-instance-methods=false;</additionalCompilerOptions>
```

### Prevent renaming of protected static variables {#prevent-rename-protected-static-variables}

In a release build, determines if static variables in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-static-variables=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-variables=false;</additionalCompilerOptions>
```

### Prevent renaming of protected instance variables {#prevent-rename-protected-instance-variables}

In a release build, determines if instance (non-static) variables in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-instance-variables=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-protected-instance-variables=false;</additionalCompilerOptions>
```

### Prevent renaming of protected static accessors {#prevent-rename-protected-static-accessors}

In a release build, determines if static accessors (getters and setters) in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-static-accessors=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-accessors=false;</additionalCompilerOptions>
```

### Prevent renaming of protected instance accessors {#prevent-rename-protected-instance-accessors}

In a release build, determines if instance (non-static) accessors (getters and setters) in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-instance-accessors=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-protected-instance-accessors=false;</additionalCompilerOptions>
```

### Prevent renaming of internal static methods {#prevent-rename-internal-static-methods}

In a release build, determines if static methods in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-static-methods=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-methods=false;</additionalCompilerOptions>
```

### Prevent renaming of internal instance methods {#prevent-rename-internal-instance-methods}

In a release build, determines if instance (non-static) methods in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-instance-methods=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-internal-instance-methods=false;</additionalCompilerOptions>
```

### Prevent renaming of internal static variables {#prevent-rename-internal-static-variables}

In a release build, determines if static variables in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-static-variables=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-variables=false;</additionalCompilerOptions>
```

### Prevent renaming of internal instance variables {#prevent-rename-internal-instance-variables}

In a release build, determines if instance (non-static) variables in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-instance-variables=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-internal-instance-variables=false;</additionalCompilerOptions>
```

### Prevent renaming of internal static accessors {#prevent-rename-internal-static-accessors}

In a release build, determines if static accessors (getters and setters) in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-static-accessors=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-accessors=false;</additionalCompilerOptions>
```

### Prevent renaming of internal instance accessors {#prevent-rename-internal-instance-accessors}

In a release build, determines if instance (non-static) accessors (getters and setters) in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-instance-accessors=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-internal-instance-accessors=false;</additionalCompilerOptions>
```