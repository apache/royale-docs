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

The [**mxmlc** and **compc** compilers](compiler/command-line-compiler-usage) bundled with [Apache Royale](https://royale.apache.org/) have a number of useful configuration options.

> The list below is also available by running `mxmlc -help advanced` or `compc -help advanced` in on the command line.

- `-allow-dynamic-bindings` (mxmlc only) -- Controls whether [data binding](features/data-binding) may use reflection for dynamic access.
- `-api-report` `<filename>` -- Used to generate a report of APIs used in a project.  
- `-benchmark` -- Output performance benchmark.
- `-closure-lib` `<string>`  -- Customize the version of Google Closure Library used by the framework.
- `-compiler.accessible`  -- With the SWF target, controls whether accessibility is enabled for a generated _.swf_ file.
- `-compiler.actionscript-file-encoding` `<string>` -- Specifies ActionScript file encoding. If there is no BOM in the AS3 source files, the compiler will use this file encoding. 
- `-compiler.advanced-telemetry`  -- Controls advanced telemetry data is enabled for a generated _.swf_ file, allowing more data to be accessed by Adobe Scout.
- [`-compiler.allow-abstract-classes`](compiler/compiler-options#allow-abstract-classes) -- If true, classes and methods can be declared `abstract` and must be overridden to be used.  
- [`-compiler.allow-import-aliases`](compiler/compiler-options#allow-import-aliases) -- If true, import alias syntax may be used in ActionScript code.
- [`-compiler.allow-private-constructors`](compiler/compiler-options#allow-private-constructors) -- If true, constructors can be declared private. Useful for a class with all-static methods or Singletons.  
- `-compiler.allow-private-name-conflicts`  
- `-compiler.allow-source-path-overlap` -- Checks if a source-path entry is a subdirectory of another source-path entry. It helps make the package names of MXML components unambiguous.
- `-compiler.allow-subclass-overrides`  
- `-compiler.as3` -- With the SWF target, use the ActionScript 3 class based object model for greater performance and better error reporting. In the class based object model most built-in functions are implemented as fixed methods of classes.
- `-compiler.binding-event-handler-class` `<string>`  
- `-compiler.binding-event-handler-event` `<string>`  
- `-compiler.binding-event-handler-interface` `<string>`  
- `-compiler.binding-value-change-event` `<string>`  
- `-compiler.binding-value-change-event-kind` `<string>`  
- `-compiler.binding-value-change-event-type` `<string>`  
- `-compiler.byte-array-embed-class` `<string>`  
- `-compiler.component-factory-class` `<string>`  
- `-compiler.component-factory-interface` `<string>`  
- `-compiler.compress` -- With the SWF target, enables or disables _.swf_ file compression.
- `-compiler.context-root` `<context-path>` -- Path to replace `{context.root}` tokens for service channel endpoints.
- `-compiler.debug` -- Determines if the compiler generates a debug or release build.
- `-compiler.defaults-css-files` `[filename]` `[...]`  
- `-compiler.defaults-css-url` `<string>` -- Defines the location of the default style sheet. Setting this option overrides the implicit use of the defaults.css style sheet in the framework SWC file.
- `-compiler.define` `<name>` `<value>` -- Define a global conditional compilation definition (i.e. `COMPILE::JS`, `CONFIG::debug`)
- `-compiler.enable-runtime-design-layers`  
- `-compiler.es` -- With the SWF target, use the ECMAScript edition 3 prototype based object model to allow dynamic overriding of prototype properties. In the prototype based object model built-in functions are implemented as dynamic properties of prototype objects.
- `-compiler.exclude-defaults-css-files` `[filename]` `[...]`  
- `-compiler.external-library-path` `[path-element]` `[...]` -- List of SWC files or directories to compile against but to omit from linking.
- `-compiler.fonts.advanced-anti-aliasing` -- With the SWF target, enables advanced anti-aliasing for embedded fonts, which provides greater clarity for small fonts.
- `-compiler.fonts.languages.language-range` `<lang>` `<range>` -- A range to restrict the number of font glyphs embedded into the SWF.
- `-compiler.fonts.local-font-paths` `[path-element]` `[...]`  
- `-compiler.fonts.local-fonts-snapshot` `<string>` -- File containing system font data produced by flex2.tools.FontSnapshot.
- `-compiler.fonts.managers` `[manager-class]` `[...]` -- Compiler font manager classes, in policy resolution order.
- `-compiler.fonts.max-cached-fonts` `<string>` -- Sets the maximum number of fonts to keep in the server cache. The default value is 20.
- `-compiler.fonts.max-glyphs-per-face` `<string>` -- Sets the maximum number of character glyph-outlines to keep in the server cache for each font face. The default value is 1000.
- `-compiler.fxg-base-class` `<string>`  
- `-compiler.headless-server` -- A flag to set when Royale is running on a server without a display.
- `-compiler.include-libraries` `[library]` `[...]` -- A list of libraries (SWCs) to completely include into the output.
- [`-compiler.infer-types`](compiler/compiler-options#infer-types) -- Allows omitting type annotations on variables by inferring the type from the right side of assignments.
- `-compiler.info.royale`  
- `-compiler.isolate-styles` -- Enables the compiled application or module to set styles that only affect itself and its children.
- [`-compiler.js-define`](compiler/compiler-options#js-define) -- Overrides `-define` for JavaScript targets.
- `-compiler.js-external-library-path` `[path-element]` `[...]`  -- Overrides `-external-library-path` for JavaScript targets. 
- `-compiler.js-library-path` `[path-element]` `[...]` -- Overrides `-library-path` for JavaScript targets.
- `-compiler.js-namespaces.namespace` `[uri]` `[manifest]` `[...]` -- Overrides `-namespace` for JavaScript targets.
- `-compiler.keep-all-type-selectors` -- Disables the pruning of unused CSS type selectors.
- `-compiler.keep-as3-metadata` `[name]` `[...]` -- Keep the specified metadata in the output.
- `-compiler.keep-code-with-metadata` `[name]` `[...]`  
- `-compiler.library-path` `[path-element]` `[...]` -- List of SWC files or directories that contain SWC files.
- `-compiler.locale` `[locale-element]` `[...]` -- Specifies the locale for internationalization.
- `-compiler.minimum-supported-version` `<string>`  
- `-compiler.mobile` -- Specifies the target runtime is a mobile device.
- `-compiler.mxml.children-as-data`  
- `-compiler.mxml.compatibility-version` `<version>` -- Specifies a compatibility version. e.g. -compatibility-version=2.0.1.
- `-compiler.mxml.force-local-id`  
- `-compiler.mxml.imports` `[implicit-import]` `[...]`  
- `-compiler.mxml.minimum-supported-version` `<string>`  
- `-compiler.namespaces.namespace` `[uri]` `[manifest]` `[...]` -- Specify a URI to associate with a manifest of components for use as MXML elements. 
- `-compiler.omit-trace-statements` -- Toggle whether `trace()` statements are omitted.
- `-compiler.optimize` -- Optimizes the bytecode of a generated _.swf_ file.
- `-compiler.preloader` `<string>` -- Specifies the default value for the Application's preloader attribute.
- `-compiler.proxy-base-class` `<string>`  
- `-compiler.remove-dead-code`  
- `-compiler.report-invalid-styles-as-warnings` -- Enables reporting of invalid styles as warnings.
- `-compiler.report-missing-required-skin-parts-as-warnings` -- Use this option to generate a warning instead of an error when a missing required skin part is detected.
- `-compiler.services` `<filename>` -- Path to BlazeDS configuration file
- `-compiler.show-actionscript-warnings` -- Runs the AS3 compiler in a mode that detects legal but potentially incorrect code.
- [`-compiler.show-binding-warnings`](compiler/compiler-options#show-binding-warnings) -- toggle whether warnings generated from [data binding](features/data-binding) code are displayed.
- `-compiler.show-invalid-css-property-warnings` -- Toggle whether invalid css property warnings are reported.
- `-compiler.show-multiple-definition-warnings`  
- `-compiler.show-shadowed-device-font-warnings` -- Toggles whether warnings are displayed when an embedded font name shadows a device font name.
- `-compiler.show-unused-type-selector-warnings` -- Toggle whether warnings generated from unused CSS type selectors are displayed.
- `-compiler.source-path` `[path-element]` `[...]` -- List of directory path elements that form the roots of ActionScript class hierarchies.
- `-compiler.states-class` `<string>`  
- `-compiler.states-event-override-class` `<string>`  
- `-compiler.states-instance-override-class` `<string>`  
- `-compiler.states-property-override-class` `<string>`  
- `-compiler.states-style-override-class` `<string>`  
- `-compiler.strict` -- Runs the AS3 compiler in strict error checking mode.
- [`-compiler.strict-identifier-names`](compiler/compiler-options#strict-identifier-names) -- Toggles whether identifier names may be keywords or not.
- `-compiler.strict-xml` -- Enables stricter rules for XML and E4X.
- `-compiler.swf-external-library-path` `[path-element]` `[...]` -- Overrides `-external-library-path` for the SWF target.
- `-compiler.swf-library-path` `[path-element]` `[...]` -- Overrides `-library-path` for JavaScript targets.
- [`-compiler.targets` `[target]` `[...]`](compiler/compiler-options#targets) -- List of target output formats (i.e. SWF, JSRoyale).
- `-compiler.theme` `[filename]` `[...]` -- List of CSS or SWC files to apply as a theme.
- `-compiler.verbose-stacktraces` -- Save callstack information to the SWF for debugging.
- `-compiler.warn-array-tostring-changes` -- Warn that Array.toString() format has changed from AS2.
- `-compiler.warn-assignment-within-conditional`  -- Warn that an assignment exists within a conditional.
- `-compiler.warn-bad-array-cast` -- Possibly invalid Array cast operation.
- `-compiler.warn-bad-bool-assignment` -- Non-Boolean value used where a Boolean value was expected.
- `-compiler.warn-bad-date-cast` -- Invalid Date cast operation.
- `-compiler.warn-bad-es3-type-method` -- Unknown method.
- `-compiler.warn-bad-es3-type-prop` -- Unknown property.
- `-compiler.warn-bad-nan-comparison` -- Illogical comparison with NaN. Any comparison operation involving NaN will evaluate to false because NaN != NaN.
- `-compiler.warn-bad-null-assignment` -- Impossible assignment to null.
- `-compiler.warn-bad-null-comparison` -- Illogical comparison with null.
- `-compiler.warn-bad-undefined-comparison` -- Illogical comparison with undefined.  Only untyped variables (or variables of type *) can be undefined.
- `-compiler.warn-boolean-constructor-with-no-args` -- Boolean() with no arguments returns false in ActionScript 3.0.  Boolean() returned undefined in ActionScript 2.0.
- `-compiler.warn-changes-in-resolve` -- `__resolve` is no longer supported. 
- `-compiler.warn-class-is-sealed` -- Class is sealed. It cannot have members added to it dynamically.
- `-compiler.warn-const-not-initialized` -- Constant not initialized.
- `-compiler.warn-constructor-returns-value` -- Function used in new expression returns a value. Result will be what the function returns, rather than a new instance of that function.
- `-compiler.warn-deprecated-event-handler-error` -- EventHandler was not added as a listener.
- `-compiler.warn-deprecated-function-error` -- Unsupported ActionScript 2.0 function.
- `-compiler.warn-deprecated-property-error` -- Unsupported ActionScript 2.0 property.
- `-compiler.warn-duplicate-argument-names` -- More than one argument by the same name.
- `-compiler.warn-duplicate-variable-def`  
- `-compiler.warn-for-var-in-changes` -- ActionScript 3.0 iterates over an object's properties within a "for x in target" statement in random order.
- `-compiler.warn-import-hides-class` -- Importing a package by the same name as the current class will hide that class identifier in this scope.
- `-compiler.warn-instance-of-changes` -- Use of the instanceof operator. 
- `-compiler.warn-internal-error` -- Internal error in compiler.
- `-compiler.warn-level-not-supported` -- `_level` is no longer supported. For more information, see the flash.display package.
- `-compiler.warn-missing-namespace-decl` -- Missing namespace declaration (e.g. variable is not defined to be public, private, etc.).
- `-compiler.warn-negative-uint-literal` -- Negative value will become a large positive value when assigned to a uint data type.
- `-compiler.warn-no-constructor` -- Missing constructor.
- `-compiler.warn-no-explicit-super-call-in-constructor` -- The `super()` statement was not called within the constructor.
- `-compiler.warn-no-type-decl` -- Missing type declaration.
- `-compiler.warn-number-from-string-changes` -- In ActionScript 3.0, white space is ignored and '' returns 0. Number() returns NaN in ActionScript 2.0 when the parameter is '' or contains white space.
- `-compiler.warn-scoping-change-in-this` -- Change in scoping for the this keyword. Class methods extracted from an instance of a class will always resolve this back to that instance. In ActionScript 2.0 this is looked up dynamically based on where the method is invoked from.
- `-compiler.warn-slow-text-field-addition` -- Inefficient use of += on a TextField.  
- `-compiler.warn-this-within-closure` -- Use of `this` within a closure may not point to expected object.
- `-compiler.warn-unlikely-function-value` -- Possible missing parentheses.
- `-compiler.warn-xml-class-has-changed` -- Possible usage of the ActionScript 2.0 XML class.
- `-debug-password` `<string>` -- With the SWF target, the password to include in debuggable _.swf_ files.
- `-default-background-color` `<int>` -- Sets the initial stage color of a generated _.swf_ file (may be overridden by the application code).
- `-default-frame-rate` `<int>` -- Sets the initial frame rate of a generated _.swf_ file (may be overridden by the application code).
- `-default-script-limits` `<max-recursion-depth>` `<max-execution-time>` -- Sets the default script execution limits of a generated _.swf_ file (may be overridden by root attributes).
- `-default-size` `<width>` `<height>` -- Sets the default stage width and height of a generated _.swf_ file.
- `-dependency-graph` `<filename>`
- `-directory` (compc only) -- Output the library as an open directory instead of a SWC file.
- `-dump-config` `<filename>` -- Write a file containing all currently set configuration values in a format suitable for use as a Royale config XML file.
- `-error-problems` `[class]` `[...]` -- Specifies the fully qualified class names of compiler problems that should be reported as errors.
- `-exclude-native-js-libraries`  
- [`-export-internal-symbols`](compiler/compiler-options#export-internal-symbols)
- [`-export-protected-symbols`](compiler/compiler-options#export-protected-symbols)
- [`-export-public-symbols`](compiler/compiler-options#export-public-symbols)
- `-external-js-lib` `[path-element]` `[...]`  
- `-externs` `[symbol]` `[...]` -- A list of symbols to omit from linking when building the output.
- `-externs-report` `<filename>` (mxmlc only)
- `-frames.frame` `[label]` `[classname]` `[...]` -- A SWF frame label with a sequence of classnames that will be linked onto the frame.
- `-help` `[keyword]` `[...]` -- Displays compiler usage instructions.
- [`-html-output-filename` `<filename>`](compiler/compiler-options#html-output-filename) - Specifies the file name of the HTML file generated by the compiler (default: _index.html_)
- [`-html-template` `<filename>`](compiler/compiler-options#html-template) -- The path to an optional template for the HTML file generated by the compiler.
- `-ignore-problems` `[class]` `[...]` -- Ignores specific problems reported by the compiler.
- `-include-classes` `[class]` `[...]` (compc only) -- A list of classes to include in the output SWC.
- `-include-file` `[name]` `[path]` `[...]` (compc only) -- A list of named files to include in the output SWC.
- `-include-inheritance-dependencies-only` -- Only include inheritance dependencies of classes specified with `-include-classes`.
- `-include-namespaces` `[uri]` `[...]` (compc only) -- All classes in the listed namespaces are included in the output SWC.
- `-include-resource-bundles` `[bundle]` `[...]` -- A list of resource bundles to include in the output.
- `-include-sources` `[path-element]` `[...]` (compc only) -- A list of directories and source files to include in the output SWC.
- `-include-styleshehet` `[name]` `[path]` `[...]` (compc only) -- A list of named stylesheet resources to include in the output SWC.
- `-includes` `[symbol]` `[...]` A list of symbols to always link into the output.
- [`-inline-constants`](compiler/compiler-options#inline-constants) -- Replace references to constants in compiled output with their literal values instead.
- `-js-compiler-define` `<name>` `<value>`  
- [`-js-compiler-option` `[option]` `[...]`](compiler/compiler-options#js-compiler-option) -- Additional options to pass to Google Closure Compiler.
- `-js-complex-implicit-coercions`  
- [`-js-default-initializers`](compiler/compiler-options#js-default-initializers) -- With JavaScript targets, determines if uninitialized variables are automatically initialized with default values.
- [`-js-dynamic-access-unknown-members`](compiler/compiler-options#js-dynamic-access-unknown-members) - With JavaScript targets, replaces `.memberName` member access with `["memberName"]` dynamic access, if the member is unrecognized to prevent Google Closure Compiler from renaming the member.
- `-js-getter-prefix` `<string>` -- Sets the string used as a prefix for getter functions in the generated _.js_ files.
- [`-js-load-config` `<filename>`](compiler/compiler-options#js-load-config) -- Overrides `-load-config` for JavaScript targets.
- [`-js-output` `<filename>`](compiler/compiler-options#js-output) -- Sets the output directory path of the generated _.js_ files.
- `-js-output-optimization` `[optimization]` `[...]`  
- `-js-output-type` `<string>` -- No longer used.
- `-js-resolve-uncertain`  
- `-js-setter-prefix` `<string>` -- Sets the string used as a prefix for setter functions in the generated _.js_ files. 
- [`-js-vector-emulation-class` `<string>`](compiler/compiler-options#js-vector-emulation-class) -- Sets the type used to emulate the ActionScript 3.0 `Vector` class in the generated _.js_ files.
- `-js-vector-index-checks`  
- [`-jsx-factory` `<string>`](compiler/compiler-options#jsx-factory)
- [`-keep-asdoc`](compiler/compiler-options#keep-asdoc)
- `-link-report` `<filename>` -- Generates an XML linkage report of the definitions linked into the output.
- `-load-config` `<filename>` -- Loads an XML configuration file that specifies more compiler options to use.
- `-load-externs` `<filename>` -- An XML file containing `<def>`, `<pre>`, and `<ext>` symbols to omit from linking when building the output.
- `-marmotinni` `<string>`  
- `-metadata.contributor` `<name>` -- A contributor's name to store in the SWF metadata.
- `-metadata.creator` `<name>` -- A creator's name to store in the SWF metadata.
- `-metadata.date` `<text>` -- The creation date to store in the SWF metadata.
- `-metadata.dateFormat` `<text>`  
- `-metadata.description` `<text>` -- The default description to store in the SWF metadata. 
- `-metadata.language` `<code>` -- The language to store in the SWF metadata (i.e. EN, FR).
- `-metadata.localized-description` `<text>` `<lang>` -- A localized RDF/XMP description to store in the SWF metadata.
- `-metadata.localized-title` `<title>` `<lang>` -- A localized RDF/XMP title to store in the SWF metadata.
- `-metadata.publisher` `<name>` -- A publisher's name to store in the SWF metadata.
- `-metadata.title` `<text>` -- The default title to store in the SWF metadata.
- `-module-output` `<filename>`  
- `-mxml-reflect-object-property` (mxmlc only)
- `-output` `<filename>` -- Sets the output path of a generated _.swf_ file.
- [`-prevent-rename-internal-instance-accessors`](compiler/compiler-options#prevent-rename-internal-instance-accessors) (mxmlc only)
- [`-prevent-rename-internal-instance-methods`](compiler/compiler-options#prevent-rename-internal-instance-methods) (mxmlc only)
- [`-prevent-rename-internal-instance-variables`](compiler/compiler-options#prevent-rename-internal-instance-variables) (mxmlc only)
- [`-prevent-rename-internal-static-accessors`](compiler/compiler-options#prevent-rename-internal-static-accessors) (mxmlc only)
- [`-prevent-rename-internal-static-methods`](compiler/compiler-options#prevent-rename-internal-static-methods) (mxmlc only)
- [`-prevent-rename-internal-static-variables`](compiler/compiler-options#prevent-rename-internal-static-variables) (mxmlc only)
- [`-prevent-rename-internal-symbols`](compiler/compiler-options#prevent-rename-internal-symbols) (mxmlc only)
- `-prevent-rename-mxml-symbol-references` (mxmlc only)
- [`-prevent-rename-protected-instance-accessors`](compiler/compiler-options#prevent-rename-protected-instance-accessors) (mxmlc only)
- [`-prevent-rename-protected-instance-methods`](compiler/compiler-options#prevent-rename-protected-instance-methods) (mxmlc only)
- [`-prevent-rename-protected-instance-variables`](compiler/compiler-options#prevent-rename-protected-instance-variables) (mxmlc only)
- [`-prevent-rename-protected-static-accessors`](compiler/compiler-options#prevent-rename-protected-static-accessors) (mxmlc only)
- [`-prevent-rename-protected-static-methods`](compiler/compiler-options#prevent-rename-protected-static-methods) (mxmlc only)
- [`-prevent-rename-protected-static-variables`](compiler/compiler-options#prevent-rename-protected-static-variables) (mxmlc only)
- [`-prevent-rename-protected-symbols`](compiler/compiler-options#prevent-rename-protected-symbols)
- [`-prevent-rename-public-instance-accessors`](compiler/compiler-options#prevent-rename-public-instance-accessors) (mxmlc only)
- [`-prevent-rename-public-instance-methods`](compiler/compiler-options#prevent-rename-public-instance-methods) (mxmlc only)
- [`-prevent-rename-public-instance-variables`](compiler/compiler-options#prevent-rename-public-instance-variables) (mxmlc only)
- [`-prevent-rename-public-static-accessors`](compiler/compiler-options#prevent-rename-public-static-accessors) (mxmlc only)
- [`-prevent-rename-public-static-methods`](compiler/compiler-options#prevent-rename-public-static-methods) (mxmlc only)
- [`-prevent-rename-public-static-variables`](compiler/compiler-options#prevent-rename-public-static-variables) (mxmlc only)
- [`-prevent-rename-public-symbols`](compiler/compiler-options#prevent-rename-public-symbols) (mxmlc only)
- `-raw-metadata` `<text>` -- XML text to store in the SWF metadata (overrides metadata.* configuration).
- [`-remove-circulars`](compiler/compiler-options#remove-circulars) -- Writes _.js_ dependencies in a way that satisfies the Google Closure Compiler. Use this if you have circular dependencies.  
- `-remove-unused-rsls` -- Remove Runtime Shared Libraries (RSLs) that are not being used by the application.
- `-resource-bundle-list` `<filename>` -- Prints a list of resource bundles to a file for input to the compc compiler to create a resource bundle SWC file.
- `-runtime-shared-libraries` `[url]` `[...]` -- A list of runtime shared library URLs to be loaded before the application starts. 
- `-runtime-shared-library-path` `[path-element]` `[rsl-url]` `[policy-file-url]` `[rsl-url]` `[policy-file-url]` -- Specifies a SWC to link against, a Runtime Shared Library (RSL) URL to load, with an optional policy file URL and optional failover URLs.
- `-runtime-shared-library-settings.application-domain` `[path-element]` `[application-domain-target]` `[...]` -- Override the application domain a Runtime Shared Library (RSL) is loaded into. The supported values are 'current', 'default', 'parent', or 'top-level'.
- `-runtime-shared-library-settings.force-rsls` `[path-element]` `[...]` -- Force a Runtime Shared Library (RSL) to be loaded, overriding the removal caused by using the remove-unused-rsls option
- `-sdk-js-lib` `[path-element]` `[...]`  
- `-size-report` `<filename>` -- Output an XML-formatted report detailing the size of all code and data linked into the application.
- [`-skip-transpile`](compiler/compiler-options#skip-transpile)
- [`-source-map`](compiler/compiler-options#source-map) -- Generate source maps for JavaScript debugging.
- [`-source-map-source-root` `<string>`](compiler/compiler-options#source-map-source-root) -- Set the source root to use for source maps used for JavaScript debugging.
- `-static-link-runtime-shared-libraries` -- Statically link the libraries specified by the `-runtime-shared-libraries-path` option.
- `-strict-publish`  
- `-swf-debugfile-alias` `<filename>`  
- `-swf-version` `<int>` -- Specifies the version of the compiled SWF file.
- `-target-player` `<version>` -- Specifies the version of the player the application is targeting. Features requiring a later version will not be compiled into the application. The minimum value supported is "9.0.0".
- `-tools-locale` `<string>` -- Specifies the locale used by the compiler when reporting errors and warnings.
- `-use-direct-blit` -- With the SWF target, use hardware acceleration to blit graphics to the screen, where such acceleration is available.
- `-use-flashbuilder-project-files`  
- `-use-gpu` -- With the SWF target, use GPU compositing features when drawing graphics, where such acceleration is available.
- `-use-network` -- Toggle whether the SWF is flagged for access to network resources.
- `-verify-digests` -- Verifies the libraries loaded at runtime are the correct ones.
- `-version` -- Display the build version of the program
- [`-warn-public-vars`](compiler/compiler-options#warn-public-vars) -- Warn for public variables that are not accessors.
- `-warning-problems` `[class]` `[...]` -- Specifies the fully qualified class names of compiler problems that should be reported as warnings.
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

Set to false to remove all [data binding](features/data-binding) warnings.

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
