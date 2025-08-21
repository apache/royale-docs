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
title: Metadata
description: Decorate classes, properties and methods with extra information that can be used at compile or run time
permalink: /features/as3/metadata
---

# Metadata

Decorate types and fields with extra information used by the compiler or with reflection

Metadata may be used to decorate classes, interfaces, properties, and methods to append extra information that may be used at compile-time or at run-time. Some predefined metadata is used by the compiler may modify the code that it generates. Custom metadata is made available to ActionScript code at run-time using [reflection](features/as3/reflection-introspection) API. The AS3 code interprets the metadata to perform specific custom functionality. With [Apache Royale](https://royale.apache.org/), you may define meta in both [AS3](features/as3) and [MXML](features/mxml).

The following example in **AS3** demonstrates decorating a public variable with `[Bindable]` metadata to make it work with [data binding](features/data-binding):

```as3
[Bindable]
public var someVariable:Boolean = true;
```

The next example in **MXML** decorates the class with `[Event]` metadata inside the special MXML `<fx:Metadata>` tag:

```mxml
<fx:Metadata>
    [Event(name="someEvent", type="org.apache.royale.events.Event")]
</fx:Metadata>
```

## Available Metadata

The following special types of metadata are available in both Royale applications and libraries.

### Alternative

Used to indicate that an alternative implementation exists for the specified definition and the user might consider switching to it instead. However, the `[Alternative]` metadata tag should not be considered as strong a signal as the `[Deprecated]` metadata tag. A definition decorated with `[Alternative]` should be considered fully supported, and it _not_ intended for removal in the future.

To specify a replacement definition for the compiler to suggest using instead, add the `replacement` field.

```as3
[Alternative(replacement="AlternateClass")]
public class OriginalClass
```

To indicate the version where the new definition was added as an alternative, add the `since` field.

```as3
[Alternative(replacement="AlternateClass", since="2.0")]
public class OriginalClass
```

### ArrayElementType

To specify that a property of type `Array` is intended to contain items of a specific type only, use `[ArrayElementType]` metadata. Normally, arrays are allowed to contain values of differing types, but the compiler will add some extra type checks if this metadata is present.

```as3
[ArrayElementType("mx.states.State")]
public var states:Array;
```

### Bindable

To reference a property using [data binding in MXML](features/data-binding), mark a property, method, or an entire class with `[Bindable]` metadata.

```as3
[Bindable]
public var selected:Boolean
```

The ActionScript compiler will automatically replace a public variable with `[Bindable]` metadata with equivalent public getter and setter methods and a private variable to store the value of the property. The generated setter method will save the value in the variable and then dispatch a `"propertyChange"` event. Royale will know to update bindings when this event is dispatched.

It is not required to use the default `"propertyChange"` event name. In fact, developers may prefer to use custom events for separate properties to improve overall performance of data binding in their applications.

The next example uses a custom `"change"` event instead of `"propertyChange"`.

```as3
private var _selected:Boolean = false;

[Bindable("change")]
public function get selected():Boolean
{
    return _selected;
}

public function set selected(value:Boolean):void
{
    if (_selected == value)
    {
        return;
    }
    _selected = value;
    dispatchEvent(new Event("change"));
}
```

When specifying a custom event name in `[Bindable]` metadata, a getter and setter is typically necsesary. The setter function should dispatch the event manually.

`[Bindable]` metadata may also be added to a method to make the result of that method available for data binding. For a method to be bindable, it must specify a custom event name. That event needs to be dispatched elsewhere in the class based on appropriate state changes inside that class.

```as3
private var _left:int = 0;
private var _right:int = 0;

[Bindable("sumChange")]
public function getSum():int
{
    return _left + _right;
}

public function setLeft(value:int):void
{
    if (_left == value)
    {
        return;
    }
    _left = value;
    dispatchEvent(new Event("sumChange"));
}

public function setRight(value:int):void
{
    if (_right == value)
    {
        return;
    }
    _right = value;
    dispatchEvent(new Event("sumChange"));
}
```

In the example above, calling either `setLeft()` or `setRight()` dispatches the `"sumChange"` event to indicate that the return value of `getSum()` has changed.

To make all properties on a class bindable, add `[Bindable]` metadata to the class itself.

```as3
[Bindable]
public class User
{
    public var name:String;
    public var dateOfBirth:Date;
    public var lockedOut:Boolean;

    public function User(name:String, dob:Date = null, lockedOut:Boolean = false)
    {
        this.name = name;
        this.dateOfBirth = dob;
        this.lockedOut = lockedOut;
    }
}
```

If any of the properties change, the `"propertyChange"` event will be dispatched, similar to if you added `[Bindable]` to each individual property.

If a property is bindable, setting a subproperty does not trigger binding updates. Consider the following class:

```as3
public class Employee
{
    [Bindable]
    public var startDate:Date;

    [Bindable]
    public var endDate:Date;
}
```

In the following example, setting the `startDate` property will cause the `"propertyChange"` event to be dispatched. However, setting `startDate.month` will not because the `Date` class does not include `[Bindable]` metadata on the `month` property.

```as3
var jim:Employee = new Employee();
jim.startDate = new Date(1990, 4, 16); // dispatches propertyChange
jim.startDate.month = 8; // does not dispatch propertyChange
```

### ChangeEvent

ChangeEvent

### CollapseWhiteSpace

A property of type `String` may be marked with `[CollapseWhiteSpace]` to indicate to the MXML parser that whitespace should be collapsed. Between each word, all whitespace characters (including spaces, tabs, new lines, and multiple consecutive whitespace characters) are replaced with a single space.

```as3
[CollapseWhiteSpace]
public var htmlText:String;
```

### Deprecated

If a definition (such as a class, interface, property, or method) is considered deprecated, and may be removed in the future, it may be marked with `[Deprecated]` metadata.

```as3
[Deprecated]
public var oldAndBusted:String;
```

To optionally include a custom deprecation message, add the `message` field.

```as3
[Deprecated(message="This message describes the deprecation")]
public var oldAndBusted:String;
```

Alternatively, pass the message as the only metadata parameter without a name.

```as3
[Deprecated("This message describes the deprecation")]
public var oldAndBusted:String;
```

To specify a replacement definition for the compiler to suggest using instead, add the `replacement` field.

```as3
[Deprecated(replacement="newHotness")]
public var oldAndBusted:String;
```

To indicate the version where the definition was deprecated, add the `since` field.

```as3
[Deprecated(replacement="newHotness", since="2.0")]
public var oldAndBusted:String;
```

Note: Metadata cannot be added to other metadata, so it is not possible to add `[Deprecated]` to `[Event]`,`[Style]`, or `[Effect]` metadata. Instead, the `deprecatedMessage`, `deprecatedReplacement`, and `deprecatedSince` fields may be added to `[Event]`,`[Style]`, or `[Effect]` metadata to indicate its deprecation status.

```as3
[Event(name="change", type="org.apache.royale.events.Event", deprecatedMessage="This message describes the deprecation")]
```

### DefaultProperty {#default-property}

The default property used when additional MXML content appears within an element's definition in an MXML file.

For example, [Jewel Group](component-sets/jewel/group) defines `[DefaultProperty("mxmlContent")]` in its class code. When using this component, instead of writting:

```mxml
<j:Group>
    <j:mxmlContent>
        <j:Button/>
    </j:mxmlContent>
</j:Group>
```

we can simplify declarations by removing `mxmlContent` tags saving several lines of code:

```mxml
<j:Group>
    <j:Button/>
</j:Group>
```

### DiscouragedForProfile

Used by the SWF target to indicate that a property is discouraged for use in specific Adobe AIR profiles.

### Effect

Apache Flex uses `[Effect]` metadata on an ActionScript component to define effects that play when triggered by events.

```as3
[Effect(name="addedEffect", event="added")]
```

The `name` field is used to define a style used to set the effect from CSS. The `event` field is used to specify the event that triggers the effect.

Royale does not currently use `[Effect]` metadata.

### Embed

Used by the SWF target to embed files (such as images, text, or binary data) into the generated _.swf_ file.

### Event

When a class extends `EventDispatcher` or implements `IEventDispatcher`, use `[Event]` metadata to define the available event constants. This metadata is used by the compiler to validate MXML, and it may be used by developer tools to provide additional code intelligence.

The `Button` class in the Basic component set defines a `click` event.

```as3
[Event(name="click", type="org.apache.royale.events.MouseEvent")]
```

The `type` field of `[Event]` metadata refers to the fully-qualified class name of the object passed to the event listener function. The `name` field specifies the event's string identifier.

In the example below, the value of the `[Event]` metadata's `name` field is used to listen for an event in MXML.

```mxml
<js:Button click="onClick(event)"/>
```

The `onClick` method is defined below. It accepts one argument of type `MouseEvent`, as defined by the `type` field of the `[Event]` metadata.

```mxml
<fx:Script>
    <![CDATA[
        import org.apache.royale.events.MouseEvent;

        private function onClick(event:MouseEvent):void
        {
            trace("clicked the button!");
        }
    ]]>
</fx:Script>
```

Similarly, the value of the `[Event]` metadata's `name` field is used to listen for an event in ActionScript using the `addEventListener()` method.

```as3
button.addEventListener("click", onClick);
```

### Exclude

Add one or more `[Exclude]` metadata tags to a class to inform developer tools that a definition inside the class should not be displayed to the user. For example, in an ActionScript or MXML code editor, the property or method may be excluded from auto-completion. 

When adding `[Exclude]` metadata, it should include two fields, `name`, and `kind`. The `name` should be the name of the definition to exclude, such as a property or method name. The `kind` field may be set to one of the following values to indicate the type of definition being excluded (it may be technically possible for definitions of different kinds to  share the same name without errors):

- `property`
- `method`
- `event`
- `style`
- `effect`

The following example excludes the `alpha` property defined in `UIBase` from a class that extends `UIBase`.

```as3
[Exclude(name="alpha", kind="property")]
public class MyComponent extends UIBase
```

Similarly, the next example excludes the `addElement` method defined in `UIBase` from a class that extends `UIBase`.

```
[Exclude(name="addElement", kind="method")]
public class MyComponent extends UIBase
```

### ExcludeClass

Add `[ExcludeClass]` metadata to a class to inform developer tools that it should not be displayed to the user in certain context. For example, in an ActionScript or MXML code editor, the class should be excluded from auto-completion. Similarly, in a visual drag-and-drop editor, the class should be excluded from available components that may be dragged into the canvas.

### Experimental

Add `[Experimental]` metadata to a definition to mark it as experimental. This metadata indicates that the definition's API signatures and behavior should be considered unstable, meaning that it is subject to change without notice in future updates, it may contain bugs, and it may not be safe to rely upon the definition in production environments.

```as3
[Experimental]
public class ExperimentalClass
```

### Frame

Used by the SWF target to append a preloader class to the generated _.swf_ file. In the second frame, the main class will become accessible through reflection.

```as3
[Frame(factoryClass="com.example.Preloader")]
public class Main extends Sprite
```

### HostComponent

The SparkRoyale component set that emulates classes from Apache Flex uses `[HostComponent]` metadata on skin classes to indicate which component class that the skin is intended to be used with.

```as3
<fx:Metadata>
    [HostComponent("spark.components.Button")]
</fx:Metadata> 
```

### IconFile

Indicates the location of an image file to use as an icon for a component. Typically used by design or developer tools to enhance the component name with a visual icon representing the component's appearance.

```
[IconFile("Canvas.png")]
public class Canvas extends Container implements IConstraintLayout
```

### Inspectable

To give hints to visual developer tools about how a property may be modified, use `[Inpectable]` metadata. Depending on the type of the property, different fields are commonly used. These fields are not strictly defined or checked by the compiler. The fields of `[Inspectable]` metadata are more of a loose convention originally used by Adobe's various visual design tools that integrated with ActionScript components.

For example, the following metadata might be added to the `alpha` property, which determines the opacity of the component. The `minValue` and `maxValue` fields may be use to restrict the range between `0.0` an `1.0`.

```as3
[Inspectable(category="General", defaultValue="1.0", minValue="0.0", maxValue="1.0")]
public function get alpha():Number
```

The `String` type is commonly used for enumerations in ActionScript 3. For properties of type `String` that should be set to one of a limited set of values, use the `enumeration` field. Each value should be separated by a comma (`,`) character.

```as3
[Inspectable(category="General", enumeration="left,right,center", defaultValue="left")]
public function get align():String
```

To restrict a property typed as `Array` to contain a single type only, add the `arrayType` field, which may be set to the fully-qualified name of a class or interface. Normally, arrays are allowed to contain values of differing types.

```as3
[Inspectable(category="General", arrayType="org.apache.royale.collections.ISortField")]
public function get fields():Array
```

The `defaultValue` field is optional, but it may be used to set a default value for the property.

- `Boolean` properties may use `true` or `false`.
- `Number` properties may use valid numeric values like `2.0` or `-5`.
- `String` properties may use any valid string, but if the `enumeration` field also exists, the default should be one of the specified values.
- `int` properties may use a valid positive or negative integer value like `3` or `-12`.
- `uint` properties may use a valid positive numeric value like `0` or `10000000`.

The `category` field is optional, but may be used by developer tools to determine how properties should be organized when displayed in a list to a user. There are several commonly used categories in Flex and Royale.

- `Advanced`
- `Data`
- `Display`
- `Effects`
- `Events`
- `Errors`
- `General`
- `Other`
- `Size`
- `Styles`
- `Text`

Some tools may automatically display all properties with `[Inspectable]` metadata in a more prominent view. To configure certain properties with `[Inspectable]` metadata, but to prevent them from being displayed prominently, set the `verbose` field to `1`.

```as3
[Inspectable(defaultValue="1.0", category="General", verbose="1", minValue="0.0", maxValue="1.0")]
public function get alpha():Number
```

To ensure that a property is _never_ displayed by visual developer tools, set the `environment` field to `none`.

```as3
[Inspectable(environment="none")]
public function get data():Object;
```

### InstanceType

InstanceType

## JSIncludeAsset

_Available since Royale 0.9.13_

Royale applications that target JavaScript may sometimes rely on third-party libraries and stylesheets. The Royale compiler provides a way to copy any additional asset files required by these _.js_ and _.css_ files to the output directory relative to the generated _index.html_ file. For example, a third-party library might require PNG or JPEG image files, or `@font-face` CSS may reference [web font](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Text_styling/Web_fonts) files, or the library may load [JSON](https://developer.mozilla.org/en-US/docs/Glossary/JSON) or [XML](https://developer.mozilla.org/en-US/docs/Glossary/XML) configuration files.

```as3
[JSIncludeAsset(source="myimage.png")]
public class MyClass
```

In the output directory, typically _bin/js-debug_ or _bin/js-release_, the _index.html_ file will be generated in the root, and asset files will be copied into an _assets_ sub-directory.

## JSIncludeCSS

_Available since Royale 0.9.13_

Royale applications that target JavaScript may sometimes rely on third-party stylesheets that don't need to be processed for use in MXML. The Royale compiler provides a way to copy additional _.css_ files to the output directory relative to the generated _index.html_ file, and it will automatically generate `<link rel="stylesheet">` elements in the HTML `<head>` section.

Add `[JSIncludeCSS]` metadata to an ActionScript class, and set the `source` field to the path of a _.css_ file. Relative paths are resolved in relation to the file that contains the metadata.

```as3
[JSIncludeCSS(source="mystyles.css")]
public class MyClass
```

In the output directory, typically _bin/js-debug_ or _bin/js-release_, the _index.html_ file will be generated in the root, and _.css_ files will be copied into a _css_ sub-directory.

## JSIncludeScript

_Available since Royale 0.9.13_

Royale applications that target JavaScript may sometimes rely on third-party libraries or scripts that are not written in ActionScript. The Royale compiler provides a way to copy additional _.js_ files to the output directory relative to the generated _index.html_ file, and it will automatically generate `<script>` elements in the HTML `<head>` section.

Add `[JSIncludeScript]` metadata to an ActionScript class, and set the `source` field to the path of a _.js_ file.Relative paths are resolved in relation to the file that contains the metadata.

```as3
[JSIncludeScript(source="myscript.js")]
public class MyClass
```

In the output directory, typically _bin/js-debug_ or _bin/js-release_, the _index.html_ file will be generated in the root, and _.js_ files will be copied into a _scripts_ sub-directory.

### Managed

Managed

### Mixin

Mixin

### NonCommittingChangeEvent

NonCommittingChangeEvent

### PercentProxy

The `width` property of `UIBase` accepts a `Number` value, measured in pixels.

```mxml
<js:Button width="32.0"/>
```

The `percentWidth` property of `UIBase` accepts a `Number` value between `0.0` and `100.0`.

```mxml
<js:Button percentWidth="100.0"/>
```

However, for convenience, the `width` property may be set to a percentage string, and the MXML compiler will automatically pass the value (without the `%` symbol to `percentWidth`).

```mxml
<js:Button width="100%"/>
```

In the UIBase class, the `width` property includes `[PercentProxy("percentWidth")]` metadata.

```as3
[PercentProxy("percentWidth")]
override public function get width():Number
```

### RemoteClass

When a serialized representation of a class instance is passed between client and server, if the ActionScript class defines `[RemoteClass]` metadata, its type information will be preserved.

```as3
package com.example {
    [RemoteObject]
    public class ValueObject
```

An optional `alias` field my be added to `[RemoteClass]` metadata to change the serialized name of the type, instead of using the fully-qualified name of the ActionScript class. For example, the alias might be a Java type name from the server that is different from the ActionScript type name on the client (Java is used as an example, and no specific language is required to be used on the server).

```as3
package org.apache.royale.collections {
    [RemoteClass(alias="flex.messaging.io.ArrayList")]
    public class ArrayList extends EventDispatcher implements IList, IExternalizable
```

### ResourceBundle

ResourceBundle

### RichTextContent

When a property in ActionScript is type as either `Object` or `*`, the MXML interpreter will attempt to guess which type to use when parsing the properties value. For instance, a value of `1.0` in MXML will be detected as a `Number` and a value of `true` will be detected as `Boolean`. To force the MXML parser to always interpret the value as a `String` instead, add `[RichTextContent]` metdata to the property definition.

```as3
[RichTextContent]
public var content:Object;
```

### SkinPart

The SparkRoyale component set that emulates classes from Apache Flex uses `[SkinPart]` metadata on an ActionScript component to define specific features that skins for that component properties are required to provide.

```as3
public class ComboBox extends DropDownListBase {
    [SkinPart(required="false")]
    public var textInput:TextInput;
```

### SkinState

The SparkRoyale component set that emulates classes from Apache Flex uses `[SkinState]` metadata on an ActionScript component to define specific states that skins for that component properties are required to provide.

```as3
[SkinState("normal")]
[SkinState("disabled")]
public class SkinnableContainerBase extends SkinnableComponent
```

### Style

The MXRoyale component set that emulates classes from Apache Flex uses `[Style]` metadata to define the style names which may be accessed using the `getStyle()` and `setStyle()` method defined on the `mx.core.UIComponent` class.

```as3
[Style(name="borderColor", type="unit", format="Color" inherit="no")]
```

### SWF

Used by the SWF target to configure certain default properties of the generated _.swf_ file, including background color, frame rate, width, height, and several other advanced options.

```as3
[SWF(backgroundColor="#000000",frameRate="60",width="720",height="480")]
public class Main extends Sprite
```

### SWFOverride

The advanced `[SWFOverride]` metadata was designed to improve the unification of Royale APIs between the JS and SWF targets. For example, Royale includes common geometric types like `Point`, `Rectangle`, and `Matrix`. These may be found in the `org.apache.royale.geom` package.

The classes in the `org.apache.royale.geom` package are implemented from scratch for the JS target. However, SWF runtimes already provides their own implementations of these types in the `flash.geom` package. Ideally, Royale should be able to take advantage of these implementations, and developers should be able to use the same types, like the `org.apache.royale.geom.Point` class, when targeting both SWF and JS.

When targeting SWF, `org.apache.royale.geom.Point` extends `flash.geom.Point`. This subclass overrides the methods from `flash.geom.Point` and changes usages of `flash.geom.Point` for certain parameters and returns to `org.apache.royale.geom.Point` instead. Normally, this would result in the compiler reporting an error because the types do not match the method that is being overridden. However, `[SWFOverride]` metadata is used to specify those original types that will unify correctly in SWF bytecode.

```as3
[SWFOverride(returns="flash.geom.Point",params="flash.geom.Point",altparams="org.apache.royale.geom.Point")]
override public function add(v:org.apache.royale.geom.Point):org.apache.royale.geom.Point
```

### Transient

When a class has `[RemoteClass]` metadata, all properties are included by default in representations of instances passed between client and server. Add `[Transient]` metadata to a property to omit that property when encoding the class instance.

```as3
[Transient]
public var myProperty:String;
```

## Example of use

For example, you may create an **MXML** component that defines a new event. To make that event known to the Royale compiler that you can reference it in MXML, you insert the `[Event]` metadata tag into your component, as the following example shows:

```mxml
<fx:Metadata>
    [Event(name="someEvent",type="org.apache.royale.events.Event")]
</fx:Metadata>
```

In this example, you use metadata to make the `someEvent` event available to the MXML compiler.

In an MXML file, you insert the metadata tags either in an `<fx:Script>` block along with your ActionScript code, or in an `<fx:Metadata>` block, as the following example shows:

```mxml
<j:Group xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:j="library://ns.apache.org/royale/jewel">

    <fx:Metadata>
        [Event("enableChange",type="org.apache.royale.events.Event")]
    </fx:Metadata>

    <fx:Script>
    <![CDATA[
        private var _enable:Boolean;

        // Add the [Inspectable] metadata tag before the individual property.
        [Inspectable(defaultValue="false")]
        public function set enable(val:Boolean):void {
            _enable = val;
            this.enabled = val;

            // Define event object, initialize it, then dispatch it. 
            var eventObj:Event = new Event("enableChange");
            dispatchEvent(eventObj);
        }
    ]]>
    </fx:Script>
</j:Group>
```

When using metadata tags in ActionScript class files, you insert the metadata tag directly into the class definition; you do not use the `<fx:Metadata>` tag.
In AS3 you can use metadata as well in methods and properties of the class.

## Custom Metadata

You may define custom metadata on a class, interface, property, or method. It is accessible at run-time using [reflection](features/as3/reflection-introspection).

The following class contains custom metadata named `[ConfigValues]` with three custom arguments.

```as3
[ConfigValues(one="1",two="2",three="3")]
public class MyClass {}
```

To ensure that the custom `[ConfigValues]` metadata is available at run-time, the `-keep-as3-metadata` compiler option may be used so that it is included in the generated code.

```
-keep-as3-metadata+=ConfigValues
```

To keep multiple metadata tags, separate them by commas.

```
-keep-as3-metadata+=ConfigValues,AnotherCustomMetadata
```

To access the metadata on a class at run-time, use the `org.apache.royale.reflection.describeType()` function to get the `TypeDefinition` for the class. Then, use `retrieveMetaDataByName()` to get access specific metadata using the name (in this case, `"ConfigValues"`).

```as3
var type:TypeDefinition = describeType(MyClass);
for each(var metadata:MetaDataDefinition in type.retrieveMetaDataByName("ConfigValues"))
{
    trace(metadata.name);
    for each (var arg:MetaDataArgDefinition in metadata.args)
    {
        trace("the value of " + arg.name + " is " + arg.value);
    }
}
```

To read all metadata defined on the class, use the `metadata` property of `TypeDefinition` instead.

```as3
for each(var metadata:MetaDataDefinition in type.metadata)
{
    trace(metadata.name);
    for each (var arg:MetaDataArgDefinition in metadata.args)
    {
        trace("the value of " + arg.name + " is " + arg.value);
    }
}
```

To access metadata defined on a member of the class, find the member inside properties of `TypeDefinition` including:

- `variables` and `staticVariables` return arrays populated with `VariableDefinition` instances.
- `accessors` and `staticAccessors` return arrays populated with `AccessorDefinition` instances.
- `methods` and `staticMethods` return arrays populated with `MethodDefinition` instances.

Similar to `TypeDefinition`, these member definitions each have a `metadata` property and a `retrieveMetaDataByName()` method.
