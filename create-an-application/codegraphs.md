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
title: Using codegraphs
description: Generate application codegraphs and use framework codegraphs to ground development tools and AI models
permalink: /create-an-application/codegraphs
---

# Using codegraphs

A codegraph is a deterministic JSON description of the public declarations and
type relationships that the Royale compiler resolves for one build target. It
records classes, interfaces, functions, members, signatures, inheritance,
metadata, ASDoc, source provenance, and references between symbols. Framework
aggregates also map Maven dependencies and MXML namespace tags.

Because the compiler creates the graph, it reflects imports, external SWCs,
visibility, inheritance, metadata, and conditional compilation. Separate
JavaScript and SWF graphs describe the APIs that are actually available on each
target.

A codegraph is not a runtime call graph. It does not contain method bodies,
application control flow, or data collected while an application runs. You do
not need a codegraph to compile, run, or deploy an application.

## Why codegraphs are useful

Development tools can use codegraphs without reparsing ActionScript and MXML
source. For example, a tool can:

* provide completion and navigation;
* find inherited members and related types;
* resolve MXML tags to their ActionScript classes;
* generate API documentation;
* compare public APIs between releases; and
* identify APIs that are available only for JavaScript or SWF.

Codegraphs are particularly useful for AI-assisted development. A general AI
model may know little about the version of Royale used by an application, may
confuse Royale APIs with Apache Flex APIs, or may invent members that sound
plausible. A codegraph supplies compiler-resolved facts that a tool can retrieve
and place in the model's context before asking it to explain or generate code.

This grounding can help an AI tool answer questions such as:

* Which component implements a particular interface?
* Which properties and events are available on an MXML tag?
* Is a member available for the application's current target?
* What constructor parameters or method arguments are required?
* Which package contains the type that should be imported?

The model still produces probabilistic output. The application should still be
compiled and tested, but codegraph grounding substantially reduces guessing
about API names, signatures, inheritance, and target availability.

## Consume framework codegraphs

Use the framework graph bundle that exactly matches the application's Royale
version. Released framework graphs are build metadata and are separate from the
SWCs that an application links.

| Installation | Framework codegraph location |
| --- | --- |
| Binary SDK | `$ROYALE_HOME/frameworks/codegraphs` |
| npm SDK | `<package>/royale-asjs/frameworks/codegraphs` |
| Maven | `org.apache.royale.framework:distribution:zip:codegraphs:<version>` |

The aggregate contains:

```text
index.json
mxml.json
<version>/<module>/<js|swf>/<module>.json
```

`index.json` lists modules, dependencies, available targets, shard paths, and
SHA-256 hashes. `mxml.json` maps namespace tags to graph symbols. Each module
shard contains the public API for one compiler target.

A consumer should:

1. Read `index.json` and reject unsupported schema major versions.
2. Select `js` or `swf` to match the application build.
3. Select the application's direct and transitive framework modules.
4. Load only those module shards and verify their SHA-256 hashes.
5. Read `mxml.json` when MXML tag lookup is needed.
6. Resolve relationships by stable symbol ID rather than by simple name or
   source-file path.

Do not copy the complete framework aggregate into every application or deploy
it with the application. Cache each released aggregate once by framework
version and schema version, then let projects share that cache.

## Ground an AI model

Do not send the entire framework aggregate to an AI model. It is too large and
most of it will be irrelevant to a particular question. Use the codegraphs as a
retrieval source:

1. Determine the application's framework version, target, and dependencies.
2. Resolve MXML tags, qualified names, and stable symbol IDs mentioned in the
   question or current source file.
3. Follow only useful edges, such as base types, interfaces, member parameter
   types, return types, events, and styles.
4. Convert the selected records into a compact text or structured-data context.
5. Ask the model to use only the supplied API facts and to identify any
   unresolved symbol instead of guessing.
6. Compile and test generated code.

For application-aware assistance, index the application's graph alongside the
matching framework shards. Keep the artifacts separate and compose them in the
retrieval layer through stable references. This lets the model understand both
project-specific APIs and the framework without creating a large merged copy.

Codegraphs contain API documentation and source provenance. Before sending
application graph content to an external AI service, apply the same privacy and
source-code policies that you use for application source.

## Generate an application codegraph

Generate an application graph when an editor, documentation system, analysis
tool, or AI retrieval service needs to understand the application's API. Use the
same compiler configuration, source paths, library paths, namespaces, and
conditional defines as the normal application build.

### Maven

Add the `compile-codegraph` goal to the existing Royale compiler plugin
configuration:

```xml
<plugin>
  <groupId>org.apache.royale.compiler</groupId>
  <artifactId>royale-maven-plugin</artifactId>
  <executions>
    <execution>
      <id>codegraph</id>
      <phase>prepare-package</phase>
      <goals>
        <goal>compile-codegraph</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```

The goal writes the project-owned graph beneath `target/codegraph`. Keep this
graph separate from downloaded framework graph bundles.

### Ant

An Ant application can invoke the codegraph compiler client directly. This
example assumes `ROYALE_COMPILER_HOME` identifies the compiler in the SDK and
the application already has a compiler configuration file.

```xml
<property environment="env"/>
<property name="ROYALE_HOME" value="${env.ROYALE_HOME}"/>
<property name="ROYALE_COMPILER_HOME" value="${env.ROYALE_COMPILER_HOME}"/>

<target name="codegraph-js">
    <mkdir dir="${basedir}/target/codegraph/js"/>
    <java jar="${ROYALE_COMPILER_HOME}/lib/codegraph.jar"
          fork="true" failonerror="true">
        <jvmarg value="-Xmx512m"/>
        <jvmarg value="-Droyalecompiler=${ROYALE_COMPILER_HOME}"/>
        <jvmarg value="-Droyalelib=${ROYALE_HOME}/frameworks"/>
        <arg value="-load-config=${basedir}/src/main/config/compile-js-config.xml"/>
        <arg value="-compiler.define+=COMPILE::JS,true"/>
        <arg value="-compiler.define+=COMPILE::SWF,false"/>
        <arg value="-keep-asdoc=true"/>
        <arg value="-output=${basedir}/target/codegraph/js/MyApplication.json"/>
        <arg value="${basedir}/src/main/royale/MyApplication.mxml"/>
    </java>
</target>
```

For a SWF graph, load the SWF configuration, set `COMPILE::JS` to `false` and
`COMPILE::SWF` to `true`, and use a separate output directory.

### Command line

The installed compiler provides `bin/codegraph` (`bin/codegraph.bat` on
Windows). In an SDK, the script is normally available at
`$ROYALE_HOME/js/bin/codegraph`.

```bash
$ROYALE_COMPILER_HOME/bin/codegraph \
  -load-config=/path/to/compile-js-config.xml \
  -compiler.define+=COMPILE::JS,true \
  -compiler.define+=COMPILE::SWF,false \
  -keep-asdoc=true \
  -output=target/codegraph/js/MyApplication.json \
  src/main/royale/MyApplication.mxml
```

The positional source file is optional. When present, its base name becomes the
module name and it is included as a graph root. Without it, use
`-include-sources` or `-include-classes` to configure roots; the output file's
base name becomes the module name.

| Argument | Purpose |
| --- | --- |
| `-load-config=<file>` | Load the application's normal compiler configuration. Use `+=` to append another configuration. |
| `-output=<file>` | Set the JSON output path. |
| `-compiler.define+=NAME,VALUE` | Supply conditional values, including `COMPILE::JS` and `COMPILE::SWF`. |
| `-include-sources+=<path>` | Add a source file or directory as a graph root. |
| `-include-classes+=<name>` | Add a qualified class as a graph root. |
| `-keep-asdoc=true` | Include parsed ASDoc in the graph. |
| `-create-target-with-errors=true` | Permit output after compiler errors. Omit this for trusted build metadata. |

All normal compiler path, namespace, define, and external-library options are
accepted. A graph is trustworthy only when those options match the application
artifact that it describes.