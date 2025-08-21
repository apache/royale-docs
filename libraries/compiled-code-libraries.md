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
title: Compiled Code Libraries
description: What are libraries in Royale
permalink: /libraries/compiled-code-libraries
---

# Compiled Code Libraries

Instructions on creating your own SWC libraries

## Concepts

On the most basic level, SWC libraries are just compiled [ActionScript](features/as3) classes. You need to include the necessary classes and the code will be included in your compiled SWC.

Libraries can also declare components that can be used in [MXML](features/MXML) files by referencing a namespace.

In this example, we're going to assume that you have both code and components to include.

We're also going to use [asconfigc](https://github.com/BowlerHatLLC/vscode-as3mxml/wiki/asconfig.json) to build the library.

## Building blocks
There are several files you will likely use for creating libraries.

1. manifest.xml
2. MyLibrary.as
3. defaults.css
4. compile-config.xml
5. js-compile-config.xml
6. asconfig.json

Of these files, `manifest.xml` and `defaults.css` are optional. `compile-config.xml` and `js-compile-config.xml` are technically not needed either, but using them makes it easier to compile your library.

## The Manifest
The manifest file (in our example named `manifest.xml`) is the file where you declare the components you want to make available to MXML using your namespace.

A manifest file is a very simple xml file with the following structure:

```
<?xml version="1.0"?>
<componentPackage>
    <component id="MyComponent1" class="com.example.MyComponent1"/>
    <component id="MyComponent2" class="com.example.MyComponent2"/>
</componentPackage>

```
Where the `id` of each component is the qualified name you declare in MXML and the `class` is the fully qualified class path of your class.

The namespace for your manifest is declared in `compile-config.xml` and `js-compile-config.xml` below.

## The main class file
In order for classes to be included in your SWC, you need to actually use them somewhere. Any classes which are declared in your manifest are considered "used", and they along with all their dependencies will be included. However, there will likely be other classes and utility functions which are not in the manifest that you want to include. The simplest solution for this is to have a Class which references all the classes you want included. To do this, you include `MyLibrary.as` at the root of your `src` folder and it should look like this:

```actionscript
package {
    internal class MyLibrary {
        import com.example.ClassA;ClassA;
        import com.example.ClassB;ClassB;
        import com.example.ClassC;ClassC;
        import com.example.ClassD;ClassD;
    }
}
```

Just referencing the classes like that is enough to have them included.

## The CSS file
`defaults.css` is where you declare any HTML or Royale CSS that's needed for your library. This is where you declare default [beads](features/strands-and-beads) and the like. Make sure you declare your namespace that's used for the MXML declarations of you components.

```
@namespace "library://ns.example.com/kapow";
@namespace js "library://ns.apache.org/royale/basic";

MyComponent1
{
    IBeadModel: ClassReference("com.example.ComponentModel");
    IBeadView:  ClassReference("com.example.ComponentView");
    IBeadController: ClassReference("com.example.ComponentController");
}

```
## Config XML file
The config file is a convenience file for loading compiler options. It's very helpful for libraries where you need to declare quite a bit of information. You need one config for the SWF build and another one for the JS build. The two files are quite similar.

The notable difference between the two files:
1. `compile-config.xml` has `playerglobal.swc` referenced in the `external-library-path`.
2. `compile-config.xml` has `COMPILE::SWF` as `true` while `js-compile-config.xml` has `COMPILE::JS` as `true`.
3. If you have a `lib/Foo.swc` JS [typedef (sometimes also called externs)](features/externs) dependency that you want to include, you should add the following to the `js-compile-config.xml`:

```
        <js-external-library-path append="true">
            <path-element>lib/Foo.swc</path-element>
        </js-external-library-path>

```

Note the important pieces in the config:

1. In the namespaces section, you need to list all the namespaces you are using. Each namespace has to have a uri and a reference to the manifest file that is associated with that uri. In our case, the components will be used with the namespace `library://ns.example.com/kapow`.
2. You need to include your css file using the `include-file` section. Any other accompanying files you want to include should be added there.
3. You need to reference your main class using `include-classes`.
4. You need to include the namespace(s) used with `include-namespaces`.

`compile-config.xml`:

```
<royale-config>
    <compiler>
        <accessible>false</accessible>
        
        <external-library-path>
            <path-element>playerglobal.swc</path-element>
        </external-library-path>
        <allow-subclass-overrides>true</allow-subclass-overrides>
        
        <mxml>
            <children-as-data>true</children-as-data>
        </mxml>
        <binding-value-change-event>org.apache.royale.events.ValueChangeEvent</binding-value-change-event>
        <binding-value-change-event-kind>org.apache.royale.events.ValueChangeEvent</binding-value-change-event-kind>
        <binding-value-change-event-type>valueChange</binding-value-change-event-type>

        <define>
            <name>COMPILE::SWF</name>
            <value>true</value>
        </define>
        <define>
            <name>COMPILE::JS</name>
            <value>false</value>
        </define>

        <keep-as3-metadata>
          <name>Bindable</name>
          <name>Managed</name>
          <name>ChangeEvent</name>
          <name>NonCommittingChangeEvent</name>
          <name>Transient</name>
        </keep-as3-metadata>
      
        <locale/>
        
        <library-path/>

        <namespaces>
            <namespace>
                <uri>library://ns.example.com/kapow</uri>
                <manifest>manifest.xml</manifest>
            </namespace>
        </namespaces>
        
        <source-path>
            <path-element>src</path-element>
        </source-path>
        
        <warn-no-constructor>false</warn-no-constructor>
    </compiler>
    <include-file>
        <name>defaults.css</name>
        <path>defaults.css</path>
    </include-file>
    
    <include-classes>
        <class>MyLibrary</class>
    </include-classes>

    <include-namespaces>
        <uri>library://ns.example.com/kapow</uri>
    </include-namespaces>

</royale-config>

```

`js-compile-config.xml`:
```
<royale-config>

    <compiler>
        <accessible>false</accessible>
        
        <js-external-library-path append="true">
            <path-element>lib/Foo.swc</path-element>
        </js-external-library-path>
        <allow-subclass-overrides>true</allow-subclass-overrides>
        
        <mxml>
            <children-as-data>true</children-as-data>
        </mxml>
        <binding-value-change-event>org.apache.royale.events.ValueChangeEvent</binding-value-change-event>
        <binding-value-change-event-kind>org.apache.royale.events.ValueChangeEvent</binding-value-change-event-kind>
        <binding-value-change-event-type>valueChange</binding-value-change-event-type>

        <define>
            <name>COMPILE::SWF</name>
            <value>false</value>
        </define>
        <define>
            <name>COMPILE::JS</name>
            <value>true</value>
        </define>

        <keep-as3-metadata>
          <name>Bindable</name>
          <name>Managed</name>
          <name>ChangeEvent</name>
          <name>NonCommittingChangeEvent</name>
          <name>Transient</name>
        </keep-as3-metadata>
      
        <locale/>
        
        <library-path/>

        <namespaces>
            <namespace>
                <uri>library://ns.example.com/kapow</uri>
                <manifest>manifest.xml</manifest>
            </namespace>
        </namespaces>
        
        <source-path>
            <path-element>src</path-element>
        </source-path>
        
        <warn-no-constructor>false</warn-no-constructor>
    </compiler>
    <include-file>
        <name>defaults.css</name>
        <path>defaults.css</path>
    </include-file>
    
    <include-classes>
        <class>MyLibrary</class>
    </include-classes>

    <include-namespaces>
        <uri>library://ns.example.com/kapow</uri>
    </include-namespaces>

</royale-config>

```

## Building the library
Your asconfig.json file should look like this the file below. You can use any standard compiler options you need and you can also include `SWF` in the targets section, but if you are only targeting JavaScript, it's not necessary.

```
{
    "config": "royale",
    "type": "lib",
    "compilerOptions": {
        "targets": [
            "JSRoyale"
        ],
        "external-library-path": [
            "${royalelib}/libs",
            "${royalelib}/../js/libs",
            "libs"
        ],
        "js-external-library-path": [
            "${royalelib}/js/libs",
            "${royalelib}/../js/libs",
            "libs"
        ],
        "load-config": [
            "compile-config.xml"
        ],
        "js-load-config": [
            "js-compile-config.xml"
        ],
        "include-classes": [
            "MyLibrary"
        ],
        "include-sources": [
            "src"
        ],
        "source-path": [
            "src"
        ],
        "output": "target/MyLibrary.swc"
    },
    "additionalOptions":[
            //include any options you want here
    ]
}
```