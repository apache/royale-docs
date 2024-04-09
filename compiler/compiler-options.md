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

List of all available compiler options

The [**mxmlc** and **compc** compilers](compiler) bundled with [Apache Royale](https://royale.apache.org/) have a number of useful configuration options. The list below is also available by running `mxmlc -help advanced` in a terminal.

- `-allow-dynamic-bindings` -- Controls whether data binding may use reflection for dynamic access.
- `-api-report` `<filename>` -- Used to generate a report of APIs used in a project.  
- `-closure-lib` `<string>`  -- Customize the version of Google Closure Library used by the framework.
- `-compiler.accessible`  -- Controls whether accessibility is enabled for a generated _.swf_ file.
- `-compiler.actionscript-file-encoding` `<string>`  
- `-compiler.advanced-telemetry`  -- Controls advanced telemetry data is enabled for a generated _.swf_ file, allowing more data to be accessed by  Adobe Scout.
- [`-compiler.allow-abstract-classes`](compiler/compiler-options#allow-abstract-classes) -- If true, classes and methods can be declared `abstract` and must be overridden to be used.  
- [`-compiler.allow-import-aliases`](compiler/compiler-options#allow-import-aliases)
- [`-compiler.allow-private-constructors`](compiler/compiler-options#allow-private-constructors) -- If true, constructors can be declared private. Useful for a class with all-static methods or Singletons.  
- `-compiler.allow-private-name-conflicts`  
- `-compiler.allow-source-path-overlap`  
- `-compiler.allow-subclass-overrides`  
- `-compiler.as3`  
- `-compiler.binding-event-handler-class` `<string>`  
- `-compiler.binding-event-handler-event` `<string>`  
- `-compiler.binding-event-handler-interface` `<string>`  
- `-compiler.binding-value-change-event` `<string>`  
- `-compiler.binding-value-change-event-kind` `<string>`  
- `-compiler.binding-value-change-event-type` `<string>`  
- `-compiler.byte-array-embed-class` `<string>`  
- `-compiler.component-factory-class` `<string>`  
- `-compiler.component-factory-interface` `<string>`  
- `-compiler.compress`  
- `-compiler.context-root` `<context-path>`  
- `-compiler.debug` -- Determines if the compiler generates a debug or release build.
- `-compiler.defaults-css-files` `[filename]` `[...]`  
- `-compiler.defaults-css-url` `<string>`  
- `-compiler.define` `<name>` `<value>` -- Allows defining compile-time constants (i.e. `COMPILE::JS`, `CONFIG::debug`)  
- `-compiler.enable-runtime-design-layers`  
- `-compiler.es`  
- `-compiler.exclude-defaults-css-files` `[filename]` `[...]`  
- `-compiler.external-library-path` `[path-element]` `[...]`  
- `-compiler.fonts.advanced-anti-aliasing`  
- `-compiler.fonts.languages.language-range` `<lang>` `<range>`  
- `-compiler.fonts.local-font-paths` `[path-element]` `[...]`  
- `-compiler.fonts.local-fonts-snapshot` `<string>`  
- `-compiler.fonts.managers` `[manager-class]` `[...]`  
- `-compiler.fonts.max-cached-fonts` `<string>`  
- `-compiler.fonts.max-glyphs-per-face` `<string>`  
- `-compiler.fxg-base-class` `<string>`  
- `-compiler.headless-server`  
- `-compiler.include-libraries` `[library]` `[...]`  
- [`-compiler.infer-types`](compiler/compiler-options#infer-types)
- `-compiler.info.royale`  
- `-compiler.isolate-styles`  
- [`-compiler.js-define`](compiler/compiler-options#js-define)
- `-compiler.js-external-library-path` `[path-element]` `[...]`  
- `-compiler.js-library-path` `[path-element]` `[...]`  
- `-compiler.js-namespaces.namespace` `[uri]` `[manifest]` `[...]`  
- `-compiler.keep-all-type-selectors`  
- `-compiler.keep-as3-metadata` `[name]` `[...]`  
- `-compiler.keep-code-with-metadata` `[name]` `[...]`  
- `-compiler.library-path` `[path-element]` `[...]`  
- `-compiler.locale` `[locale-element]` `[...]`  
- `-compiler.minimum-supported-version` `<string>`  
- `-compiler.mobile`  
- `-compiler.mxml.children-as-data`  
- `-compiler.mxml.compatibility-version` `<version>`  
- `-compiler.mxml.force-local-id`  
- `-compiler.mxml.imports` `[implicit-import]` `[...]`  
- `-compiler.mxml.minimum-supported-version` `<string>`  
- `-compiler.namespaces.namespace` `[uri]` `[manifest]` `[...]`  
- `-compiler.omit-trace-statements`  
- `-compiler.optimize` -- Optimizes the bytecode of a generated _.swf_ file.
- `-compiler.preloader` `<string>`  
- `-compiler.proxy-base-class` `<string>`  
- `-compiler.remove-dead-code`  
- `-compiler.report-invalid-styles-as-warnings`  
- `-compiler.report-missing-required-skin-parts-as-warnings`  
- `-compiler.services` `<filename>`  
- `-compiler.show-actionscript-warnings`  
- [`-compiler.show-binding-warnings`](compiler/compiler-options#show-binding-warnings)
- `-compiler.show-invalid-css-property-warnings`  
- `-compiler.show-multiple-definition-warnings`  
- `-compiler.show-shadowed-device-font-warnings`  
- `-compiler.show-unused-type-selector-warnings`  
- `-compiler.source-path` `[path-element]` `[...]`  
- `-compiler.states-class` `<string>`  
- `-compiler.states-event-override-class` `<string>`  
- `-compiler.states-instance-override-class` `<string>`  
- `-compiler.states-property-override-class` `<string>`  
- `-compiler.states-style-override-class` `<string>`  
- `-compiler.strict`  
- [`-compiler.strict-identifier-names`](compiler/compiler-options#strict-identifier-names)
- `-compiler.strict-xml` -- Enables stricter rules for XML and E4X.
- `-compiler.swf-external-library-path` `[path-element]` `[...]`  
- `-compiler.swf-library-path` `[path-element]` `[...]`  
- [`-compiler.targets` `[target]` `[...]`](compiler/compiler-options#targets)
- `-compiler.theme` `[filename]` `[...]`  
- `-compiler.verbose-stacktraces`  
- `-compiler.warn-array-tostring-changes`  
- `-compiler.warn-assignment-within-conditional`  
- `-compiler.warn-bad-array-cast`  
- `-compiler.warn-bad-bool-assignment`  
- `-compiler.warn-bad-date-cast`  
- `-compiler.warn-bad-es3-type-method`  
- `-compiler.warn-bad-es3-type-prop`  
- `-compiler.warn-bad-nan-comparison`  
- `-compiler.warn-bad-null-assignment`  
- `-compiler.warn-bad-null-comparison`  
- `-compiler.warn-bad-undefined-comparison`  
- `-compiler.warn-boolean-constructor-with-no-args`  
- `-compiler.warn-changes-in-resolve`  
- `-compiler.warn-class-is-sealed`  
- `-compiler.warn-const-not-initialized`  
- `-compiler.warn-constructor-returns-value`  
- `-compiler.warn-deprecated-event-handler-error`  
- `-compiler.warn-deprecated-function-error`  
- `-compiler.warn-deprecated-property-error`  
- `-compiler.warn-duplicate-argument-names`  
- `-compiler.warn-duplicate-variable-def`  
- `-compiler.warn-for-var-in-changes`  
- `-compiler.warn-import-hides-class`  
- `-compiler.warn-instance-of-changes`  
- `-compiler.warn-internal-error`  
- `-compiler.warn-level-not-supported`  
- `-compiler.warn-missing-namespace-decl`  
- `-compiler.warn-negative-uint-literal`  
- `-compiler.warn-no-constructor`  
- `-compiler.warn-no-explicit-super-call-in-constructor`  
- `-compiler.warn-no-type-decl`  
- `-compiler.warn-number-from-string-changes`  
- `-compiler.warn-scoping-change-in-this`  
- `-compiler.warn-slow-text-field-addition`  
- `-compiler.warn-this-within-closure`  
- `-compiler.warn-unlikely-function-value`  
- `-compiler.warn-xml-class-has-changed`  
- `-debug-password` `<string>`  
- `-default-background-color` `<int>` -- Sets the initial stage color of a generated _.swf_ file.
- `-default-frame-rate` `<int>` -- Sets the initial frame rate of a generated _.swf_ file.
- `-default-script-limits` `<max-recursion-depth>` `<max-execution-time>`  
- `-default-size` `<width>` `<height>` -- Sets the default stage width and height of a generated _.swf_ file.
- `-dependency-graph` `<filename>`  
- `-dump-config` `<filename>`  
- `-error-problems` `[class]` `[...]`  
- `-exclude-native-js-libraries`  
- [`-export-internal-symbols`](compiler/compiler-options#export-internal-symbols)
- [`-export-protected-symbols`](compiler/compiler-options#export-protected-symbols)
- [`-export-public-symbols`](compiler/compiler-options#export-public-symbols)
- `-external-js-lib` `[path-element]` `[...]`  
- `-externs` `[symbol]` `[...]`  
- `-externs-report` `<filename>`  
- `-frames.frame` `[label]` `[classname]` `[...]`  
- `-help` `[keyword]` `[...]` -- Displays compiler usage instructions.
- [`-html-output-filename` `<filename>`](compiler/compiler-options#html-output-filename)
- [`-html-template` `<filename>`](compiler/compiler-options#html-template)
- `-ignore-problems` `[class]` `[...]`
- `-include-inheritance-dependencies-only`  
- `-include-resource-bundles` `[bundle]` `[...]`  
- `-includes` `[symbol]` `[...]`  
- [`-inline-constants`](compiler/compiler-options#inline-constants)
- `-js-compiler-define` `<name>` `<value>`  
- [`-js-compiler-option` `[option]` `[...]`](compiler/compiler-options#js-compiler-option)
- `-js-complex-implicit-coercions`  
- [`-js-default-initializers`](compiler/compiler-options#js-default-initializers)
- [`-js-dynamic-access-unknown-members`](compiler/compiler-options#js-dynamic-access-unknown-members)
- `-js-getter-prefix` `<string>` -- Sets the string used as a prefix for getter functions in the generated _.js_ files.
- [`-js-load-config` `<filename>`](compiler/compiler-options#js-load-config)
- [`-js-output` `<filename>`](compiler/compiler-options#js-output) -- Sets the output directory path of the generated _.js_ files.
- `-js-output-optimization` `[optimization]` `[...]`  
- `-js-output-type` `<string>`  
- `-js-resolve-uncertain`  
- `-js-setter-prefix` `<string>` -- Sets the string used as a prefix for setter functions in the generated _.js_ files. 
- [`-js-vector-emulation-class` `<string>`](compiler/compiler-options#js-vector-emulation-class) -- Sets the type used to emulate the ActionScript 3.0 `Vector` class in the generated _.js_ files.
- `-js-vector-index-checks`  
- [`-jsx-factory` `<string>`](compiler/compiler-options#jsx-factory)
- [`-keep-asdoc`](compiler/compiler-options#keep-asdoc)
- `-link-report` `<filename>` -- Generates a linkage report of the symbols included in the output.
- `-load-config` `<filename>` -- Loads an XML configuration file that specifies more compiler options to use.
- `-load-externs` `<filename>`  
- `-marmotinni` `<string>`  
- `-metadata.contributor` `<name>`  
- `-metadata.creator` `<name>`  
- `-metadata.date` `<text>`  
- `-metadata.dateFormat` `<text>`  
- `-metadata.description` `<text>`  
- `-metadata.language` `<code>`  
- `-metadata.localized-description` `<text>` `<lang>`  
- `-metadata.localized-title` `<title>` `<lang>`  
- `-metadata.publisher` `<name>`  
- `-metadata.title` `<text>`  
- `-module-output` `<filename>`  
- `-mxml-reflect-object-property`  
- `-output` `<filename>` -- Sets the output path of a generated _.swf_ file.
- [`-prevent-rename-internal-instance-accessors`](compiler/compiler-options#prevent-rename-internal-instance-accessors)
- [`-prevent-rename-internal-instance-methods`](compiler/compiler-options#prevent-rename-internal-instance-methods)
- [`-prevent-rename-internal-instance-variables`](compiler/compiler-options#prevent-rename-internal-instance-variables)
- [`-prevent-rename-internal-static-accessors`](compiler/compiler-options#prevent-rename-internal-static-accessors)
- [`-prevent-rename-internal-static-methods`](compiler/compiler-options#prevent-rename-internal-static-methods)
- [`-prevent-rename-internal-static-variables`](compiler/compiler-options#prevent-rename-internal-static-variables)
- [`-prevent-rename-internal-symbols`](compiler/compiler-options#prevent-rename-internal-symbols)
- `-prevent-rename-mxml-symbol-references`
- [`-prevent-rename-protected-instance-accessors`](compiler/compiler-options#prevent-rename-protected-instance-accessors)
- [`-prevent-rename-protected-instance-methods`](compiler/compiler-options#prevent-rename-protected-instance-methods)
- [`-prevent-rename-protected-instance-variables`](compiler/compiler-options#prevent-rename-protected-instance-variables)
- [`-prevent-rename-protected-static-accessors`](compiler/compiler-options#prevent-rename-protected-static-accessors)
- [`-prevent-rename-protected-static-methods`](compiler/compiler-options#prevent-rename-protected-static-methods)
- [`-prevent-rename-protected-static-variables`](compiler/compiler-options#prevent-rename-protected-static-variables)
- [`-prevent-rename-protected-symbols`](compiler/compiler-options#prevent-rename-protected-symbols)
- [`-prevent-rename-public-instance-accessors`](compiler/compiler-options#prevent-rename-public-instance-accessors)
- [`-prevent-rename-public-instance-methods`](compiler/compiler-options#prevent-rename-public-instance-methods)
- [`-prevent-rename-public-instance-variables`](compiler/compiler-options#prevent-rename-public-instance-variables)
- [`-prevent-rename-public-static-accessors`](compiler/compiler-options#prevent-rename-public-static-accessors)
- [`-prevent-rename-public-static-methods`](compiler/compiler-options#prevent-rename-public-static-methods)
- [`-prevent-rename-public-static-variables`](compiler/compiler-options#prevent-rename-public-static-variables)
- [`-prevent-rename-public-symbols`](compiler/compiler-options#prevent-rename-public-symbols)
- `-raw-metadata` `<text>`  
- [`-remove-circulars`](compiler/compiler-options#remove-circulars) -- Writes _.js_ dependencies in a way that satisfies the Google Closure Compiler. Use this if you have circular dependencies.  
- `-remove-unused-rsls`  
- `-resource-bundle-list` `<filename>`  
- `-runtime-shared-libraries` `[url]` `[...]`  
- `-runtime-shared-library-path` `[path-element]` `[rsl-url]` `[policy-file-url]` `[rsl-url]` `[policy-file-url]`  
- `-runtime-shared-library-settings.application-domain` `[path-element]` `[application-domain-target]` `[...]`  
- `-runtime-shared-library-settings.force-rsls` `[path-element]` `[...]`  
- `-sdk-js-lib` `[path-element]` `[...]`  
- `-size-report` `<filename>`  
- [`-skip-transpile`](compiler/compiler-options#skip-transpile)
- [`-source-map`](compiler/compiler-options#source-map)
- [`-source-map-source-root` `<string>`](compiler/compiler-options#source-map-source-root)
- `-static-link-runtime-shared-libraries`  
- `-strict-publish`  
- `-swf-debugfile-alias` `<filename>`  
- `-swf-version` `<int>`  
- `-target-player` `<version>`  
- `-tools-locale` `<string>`  
- `-use-direct-blit`  
- `-use-flashbuilder-project-files`  
- `-use-gpu`  
- `-use-network`  
- `-verify-digests`  
- `-version`  
- [`-warn-public-vars`](compiler/compiler-options#warn-public-vars) -- Controls a compile-time warning for public variables that are not accessors.
- `-warning-problems` `[class]` `[...]`  
- `-warnings` -- Determines if compile-time warnings are enabled.
- [`-watch`](compiler/compiler-options#watch) -- Watch for source file changes and rebuild incrementally

### allow-abstract-classes {#allow-abstract-classes}

Determines if the `abstract` modifier may be used with classes. For more details, see [Abstract Classes in ActionScript](features/as3/abstract-classes).

```sh
-allow-abstract-classes
```

### allow-import-aliases {#allow-import-aliases}

Determines if alias syntax for for imported symbols is allowed or not.

```sh
-allow-import-aliases
```

### allow-private-constructors {#allow-private-constructors}

Determines if the `private` namespace may be used with class constructors. For more details, see [Private Constructors in ActionScript](features/as3/private-constructors).

```sh
-allow-private-constructors
```

### closure-lib {#closure-lib}

Sets the path to a custom distribution of Google's Closure library, instead of the default version used by the compiler.

```sh
-closure-lib path/to/closure
```

### js-define {#js-define}

Defines a global constant at compile time. May be a boolean, number, string, or expression.

```sh
-define CONFIG::debugging true -js-define CONFIG::release false
```

For boolean and numeric values, you may pass in literals like true, false, or 123. Format string values with nested quotes, like "'hello'", because the compiler will attempt to evaluate an expression when it encounters a quotation mark.

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
private static var _buildNumber:String = BUILD::buildNumber;

// Project Version
private static var _projectVersion:String = BUILD::buildVersion;
```

### html-output-filename {#html-output-filename}

Specifies the file name of the HTML file generated by the compiler to load the Apache Royale application in the browser.

```sh
-html-output-filename custom.html
```

### html-template {#html-template}

Specifies the path to an optional template for the HTML file generated by the compiler to load the Apache Royale application in the browser.

```sh
-html-template ./path/to/template.html
```

#### Maven configuration:

```xml
<htmlTemplate>${basedir}/target/javascript/bin/js-debug/jewel-example-index-template.html</htmlTemplate>
```

## infer-types {#infer-types}

Specifies that types of variables, fields, and function returns, if omitted, should be inferred from the initializer or return statements. For more details, see [Type Inference in ActionScript](features/as3/type-inference).

```sh
-infer-types
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-infer-types=true;</additionalCompilerOptions>
```

## inline-constants {#inline-constants}

Determines if primitive constant values (such as numbers, booleans, and strings) will be inlined.

```sh
-inline-constants
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-inline-constants=true;</additionalCompilerOptions>
```

### js-compiler-option {#js-compiler-option}

Specifies one or more custom compiler options to pass to the Google Closure Compiler, which is used to create the release build of an Apache Royale application.

```sh
-js-compiler-option+="--variable_map_output_file gccvars.txt" -js-compiler-option+="--compilation_level SIMPLE_OPTIMIZATIONS"
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-js-compiler-option=--variable_map_output_file gccvars.txt;-js-compiler-option+=--property_map_output_file gccprops.txt</additionalCompilerOptions>
```

### js-default-initializers {#js-default-initializers}

Defaults to true. Enables or disables initialization of primitive (Number, Boolean, etc.) variables with default values in the generated JavaScript. Corresponds to AVM runtime implicit type intialization values.

Note that some reflection utility functions require this to be set to true in order for them to work correctly in JavaScript.  

```sh
-js-default-initializers
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-js-default-initializers=true;</additionalCompilerOptions>
```

### js-define {#js-define}

Defines a global constant at compile time for the JavaScript output, but not the SWF output. May be a boolean, number, string, or expression.

```sh
-js-define CONFIG::debugging true -js-define CONFIG::release false
```

For boolean and numeric values, you may pass in literals like true, false, or 123. Format string values with nested quotes, like "'hello'", because the compiler will attempt to evaluate an expression when it encounters a quotation mark.

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
private static var _buildNumber:String = BUILD::buildNumber;

// Project Version
private static var _projectVersion:String = BUILD::buildVersion;
```

### js-dynamic-access-unknown-members {#js-dynamic-access-unknown-members}

If the definition of a member cannot be resolved at compile time, emit dynamic access instead of normal member access. Ensures that dynamic members aren't renamed.

```sh
-js-dynamic-access-unknown-members 
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-js-dynamic-access-unknown-members=true;</additionalCompilerOptions>
```

### js-load-config {#js-load-config}

Specifies the locations of XML configuration files that define extra compiler options for JavaScript output.

```sh
-js-load-config path/to/project-config.xml
```

#### Maven configuration:

### js-output {#js-output}

The path where the generated JavaScript output should be saved, if your are also using it for the .swf output path.

```sh
-js-output path/to/output
```

#### Maven configuration:

Use instead `outputDirectory` in `configuration` xml node

### js-vector-emulation-class {#js-vector-emulation-class}

A custom implemention to use instead of default emulation of the AVM2 `Vector` typed collection.

```sh
-js-vector-emulation-class=com.example.MyVectorClass
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-js-vector-emulation-class=com.example.MyVectorClass;</additionalCompilerOptions>
```

### jsx-factory {#jsx-factory}

Customize the factory to use for JSX syntax. Defaults to `React.createElement`.

```sh
-jsx-factory=_jsx
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-jsx-factory=_jsx;</additionalCompilerOptions>
```

### keep-asdoc {#keep-asdoc}

Determines if asdoc comment annotations are kept in the generated JavaScript.

```sh
-keep-asdoc=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-keep-asdoc=false;</additionalCompilerOptions>
```

### export-public-symbols {#export-public-symbols}

In a release build, determines if symbols in the `public` namespace will be exported or not. The default value is `true`.

```sh
-export-public-symbols=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-export-public-symbols=false;</additionalCompilerOptions>
```

### export-protected-symbols {#export-protected-symbols}

In a release build, determines if symbols in the `protected` namespace will be exported. The default value is `false`.

```sh
-export-protected-symbols=true
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-export-protected-symbols=true;</additionalCompilerOptions>
```

### export-internal-symbols {#export-internal-symbols}

In a release build, determines if symbols in the `internal` namespace will be exported. The default value is `false`.

```sh
-export-internal-symbols=true
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-export-internal-symbols=true;</additionalCompilerOptions>
```

### prevent-rename-public-symbols {#prevent-rename-public-symbols}

In a release build, determines if symbols in the `public` namespace may be renamed or not. The default value is `true`.

```sh
-prevent-rename-public-symbols=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

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

### prevent-rename-protected-symbols {#prevent-rename-protected-symbols}

In a release build, determines if symbols in the `protected` namespace may be renamed or not. The default value is `true`.

```sh
-prevent-rename-protected-symbols=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

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

### prevent-rename-internal-symbols {#prevent-rename-internal-symbols}

In a release build, determines if symbols in the `internal` namespace may be renamed or not. The default value is `true`.

```sh
-prevent-rename-internal-symbols=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

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

### prevent-rename-public-static-methods {#prevent-rename-public-static-methods}

In a release build, determines if static methods in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-static-methods=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-methods=false;</additionalCompilerOptions>
```

### prevent-rename-public-instance-methods {#prevent-rename-public-instance-methods}

In a release build, determines if instance (non-static) methods in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-instance-methods=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-public-instance-methods=false;</additionalCompilerOptions>
```

### prevent-rename-public-static-variables {#prevent-rename-public-static-variables}

In a release build, determines if static variables in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-static-variables=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-variables=false;</additionalCompilerOptions>
```

### prevent-rename-public-instance-variables {#prevent-rename-public-instance-variables}

In a release build, determines if instance (non-static) variables in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-instance-variables=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-public-instance-variables=false;</additionalCompilerOptions>
```

### prevent-rename-public-static-accessors {#prevent-rename-public-static-accessors}

In a release build, determines if static accessors (getters and setters) in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-static-accessors=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-accessors=false;</additionalCompilerOptions>
```

### prevent-rename-public-instance-accessors {#prevent-rename-public-instance-accessors}

In a release build, determines if instance (non-static) accessors (getters and setters) in the `public` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-public-symbols` compiler option is `false`.

```sh
-prevent-rename-public-instance-accessors=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-public-instance-accessors=false;</additionalCompilerOptions>
```

### prevent-rename-protected-static-methods {#prevent-rename-protected-static-methods}

In a release build, determines if static methods in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-static-methods=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-methods=false;</additionalCompilerOptions>
```

### prevent-rename-protected-instance-methods {#prevent-rename-protected-instance-methods}

In a release build, determines if instance (non-static) methods in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-instance-methods=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-protected-instance-methods=false;</additionalCompilerOptions>
```

### prevent-rename-protected-static-variables {#prevent-rename-protected-static-variables}

In a release build, determines if static variables in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-static-variables=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-variables=false;</additionalCompilerOptions>
```

### prevent-rename-protected-instance-variables {#prevent-rename-protected-instance-variables}

In a release build, determines if instance (non-static) variables in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-instance-variables=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-protected-instance-variables=false;</additionalCompilerOptions>
```

### prevent-rename-protected-static-accessors {#prevent-rename-protected-static-accessors}

In a release build, determines if static accessors (getters and setters) in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-static-accessors=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-accessors=false;</additionalCompilerOptions>
```

### prevent-rename-protected-instance-accessors {#prevent-rename-protected-instance-accessors}

In a release build, determines if instance (non-static) accessors (getters and setters) in the `protected` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-protected-symbols` compiler option is `false`.

```sh
-prevent-rename-protected-instance-accessors=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-protected-instance-accessors=false;</additionalCompilerOptions>
```

### prevent-rename-internal-static-methods {#prevent-rename-internal-static-methods}

In a release build, determines if static methods in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-static-methods=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-methods=false;</additionalCompilerOptions>
```

### prevent-rename-internal-instance-methods {#prevent-rename-internal-instance-methods}

In a release build, determines if instance (non-static) methods in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-instance-methods=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-internal-instance-methods=false;</additionalCompilerOptions>
```

### prevent-rename-internal-static-variables {#prevent-rename-internal-static-variables}

In a release build, determines if static variables in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-static-variables=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-variables=false;</additionalCompilerOptions>
```

### prevent-rename-internal-instance-variables {#prevent-rename-internal-instance-variables}

In a release build, determines if instance (non-static) variables in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-instance-variables=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-internal-instance-variables=false;</additionalCompilerOptions>
```

### prevent-rename-internal-static-accessors {#prevent-rename-internal-static-accessors}

In a release build, determines if static accessors (getters and setters) in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-static-accessors=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-static-accessors=false;</additionalCompilerOptions>
```

### prevent-rename-internal-instance-accessors {#prevent-rename-internal-instance-accessors}

In a release build, determines if instance (non-static) accessors (getters and setters) in the `internal` namespace may be renamed or not. The default value is `true`. This option will be ignored if the `prevent-rename-internal-symbols` compiler option is `false`.

```sh
-prevent-rename-internal-instance-accessors=false
```

> Note: This option applies only to compiling applications using `mxmlc`. If you are compiling a library (using `compc`), this option does not exist, and you will get a warning if you try to use it.

#### Maven configuration:

```xml
<additionalCompilerOptions>-prevent-rename-internal-instance-accessors=false;</additionalCompilerOptions>
```

### remove-circulars {#remove-circulars}

Tells the Apache Royale compiler to remove circular dependencies in the generated JavaScript, where possible.

```sh
-remove-circulars
```

#### Maven configuration:

```xml
<removeCirculars>true</removeCirculars>
```

### show-binding-warnings {#show-binding-warnings}

Set to false to remove all binding warnings.

```sh
-show-binding-warnings=false
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-show-binding-warnings=false;</additionalCompilerOptions>
```

### skip-transpile {#skip-transpile}

**(Advanced)** Set to false to skip transpiling ActionScript and MXML to JavaScript, and only run the release build. Generally used by contributors to the compiler only. Default s to `false`.

```sh
-skip-transpile=true
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-skip-transpile=true;</additionalCompilerOptions>
```

### strict-identifier-names {#strict-identifier-names}

Determines if names of identifiers must follow the strict rules of ActionScript 3.0, or if they may use the looser rules introduced in ECMAScript 5. Defaults to `false`.

```sh
-strict-identifier-names
```

### source-map {#source-map}

Emits a source map in the debug build for each ActionScript file. The default value is false.

```sh
-source-map
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-source-map=true;</additionalCompilerOptions>
```

### source-map-source-root {#source-map-source-root}

Sets a custom value for the `sourceRoot` property in the generated source map files. This option will be ignored if the `source-map` compiler option is `false`.

```sh
-source-map-source-root=my/custom/path
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-source-map-source-root=my/custom/path;</additionalCompilerOptions>
```

### targets {#targets}

Specifies the target format of the code generated by the Apache Royale compiler. You can specify multiple targets.

```sh
-targets JSRoyale,SWF
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
-warn-public-vars
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-warn-public-vars=true;</additionalCompilerOptions>
```

### watch {#watch}

After initial compilation completes, the compiler keeps running to watch for source file changes. When _.as_ or _.mxml_ files are changed, the compiler runs a fast incremental build. Use Ctrl+C to exit the compiler.

```sh
-watch
```

#### Maven configuration:

```xml
<additionalCompilerOptions>-watch=true;</additionalCompilerOptions>
```
