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
title: Cascading Style Sheets
description: Cascading Style Sheets reference
permalink: /css
---
# Cascading Style Sheets

Cascading Style Sheets reference.

Cascading Style Sheet (CSS) in Apache Flex is a dialect of the [CSS3 standard](https://www.w3.org/TR/css-2023/). CSS appears either in an external file or as a local CSS definition in a MXML component.

Compared to the CSS standard:

* Flex supports subclassing selectors.
* Flex supports a subset of the style properties that are available in CSS.
* Flex controls have additional unique style properties that are not defined by the CSS specification.
* Flex controls only support styles that are defined by the current theme.
* Flex style sheets can define skins for controls using the `Embed` keyword.
* The CSS 3 wildcard namespace prefix syntax of `*|` that matches any namespace is not supported.
* The universal selector scoped to a particular CSS namespace is not supported. Namespaces are not known at runtime in Flex and as such the universal selector remains universal no matter what namespace it is scoped to in CSS.
* If you apply multiple class selectors to a component, the order of preference that the styles is applied is the order in which they appear in the `styleName` property’s space-delimited list, not the order in which they are defined in the CSS block or external style sheet.

Certain explanations in this reference were taken from the "Using Flex 4.6" document and this article:

* [Using Cascading Style Sheets](https://web.archive.org/web/20120207085203/http://www.dremsus.com/index.php/category/flex-air/using-cascading-style-sheets/)

## Coding Conventions

* When applying style properties with CSS in a `<fx:Style>` block or in an external style sheet, the best practice is to use camel-case without hyphens. However, Flex supports both the camel-case and hyphenated syntax in style sheets.

## Namespaces

To distinguish between different components that share the same name, you specify namespaces in your CSS that apply to types.

The following are valid namespaces:

* URIs in the manifest of the Flex SDK
  * `library://ns.adobe.com/flex/spark`
  * `library://ns.adobe.com/flex/mx`
* Package names with a trailing `.*`, such as `com.foo.bar.*`, identifying a component set defined in ActionScript 3

For example, we can specify that a particular selector apply to all components in the Spark namespace only.

```css
@namespace s "library://ns.adobe.com/flex/spark";
```

Type selectors can then use the `s|` prefix to refer to the Spark namespace, such as in:

```css
s|Button {
    fontSize: 16;
}
```

Omitting the `ns|` prefix will use the default CSS namespace.

## Type Selectors

**Type selectors** assign styles to all components of a particular type. Flex applies the style to all classes of that type. Flex also applies the style properties defined by a type selector to all subclasses of that type.

To use type selectors we required to specify which namespace each type appears in with the `@namespace` directive.

**Example**

```xml
<?xml version="1.0"?>
<s:Application
    xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:mx="library://ns.adobe.com/flex/mx"
  	xmlns:s="library://ns.adobe.com/flex/spark">
    <fx:Style>
        @namespace s "library://ns.adobe.com/flex/spark";
        s|Button {
            fontSize: 15;
            color: #9933FF;
        }
    </fx:Style>
    <s:VGroup>
        <s:Button id="myButton" label="Click Me"/>
        <s:Button id="myButton2" label="Click Me"/>
    </s:VGroup>
</s:Application>
```

## Class Selectors

Class selectors define a set of styles (or a class) that we can apply to any component. You define the style class, and then point to the style class using the `styleName` property of the component’s MXML tag.

*Note: all components that are a subclass of the UIComponent class support the `styleName` property.*

**Example**

The following example defines a new style `myFontStyle` and applies that style to a `Button` component by assigning the Button to the `myFontStyle` style class.

```xml
<?xml version="1.0"?>
<s:Application
    xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:mx="library://ns.adobe.com/flex/mx"
  	xmlns:s="library://ns.adobe.com/flex/spark">
    <fx:Style>
        .myFontStyle {
            fontSize: 15;
            color: #9933FF;
        }
    </fx:Style>
    <s:VGroup>
        <s:Button id="myButton" styleName="myFontStyle" label="Click Me"/>
        <s:Button id="myButton2" label="Click Me"/>
    </s:VGroup>
</s:Application>
```

We can apply **multiple** class selectors by separating them with a space in the `styleName` property.

*Note: the order of preference that the styles is applied is the order in which they appear in the space-delimited list, not the order in which they are defined in the CSS block or external style sheet.*

```xml
<?xml version="1.0"?>
<s:Application
    xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:mx="library://ns.adobe.com/flex/mx"
  	xmlns:s="library://ns.adobe.com/flex/spark">
    <fx:Style>
        .myFontStyle {
            fontSize: 15;
        }
        .myOtherFontStyle {
            color: #9933FF;
        }
    </fx:Style>
    <s:VGroup>
        <s:Button id="myButton" styleName="myFontStyle myOtherFontStyle" label="Click Me"/>
        <s:Button id="myButton2" label="Click Me"/>
    </s:VGroup>
</s:Application>
```

## Inheritance

**Remarks**

1. If we set an inheritable style property on a parent container, its children inherit that style property. For example, if you define `fontFamily` as `Times` for a `Panel` container, all children of that container will also use `Times` for `fontFamily`, unless they override that property.
2. If we set a noninheritable style on a parent container, only the parent container uses that style; the children do not use that style.
3. In general, color and text styles are inheritable, regardless of which theme they are in (Spark or Halo) or how they are set (by using style sheets or the `setStyle()` method).
4. The following are exceptions to the rules of inheritance:
    1. If we use the `global` selector in a CSS style definition, Flex applies those style properties to all controls, regardless of whether the properties are inheritable.
    2. The values set in type selectors apply to the target class as well as its subclasses, even if the style properties are not inheritable. For example, if you define a `Group` type selector, Flex applies all styles in that selector to `Group` and `VGroup` controls because `VGroup` is a subclass of `Group`.
5. We should avoid using type selectors for commonly-used base classes like `Group`. Why? `Group` is a class that Spark skins are based on. Setting styles on the `Group` type selector might cause unexpected results because the skins will have styles applied that we might not ordinarily expect to apply.

```xml
<?xml version="1.0"?>
<s:Application
    xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:mx="library://ns.adobe.com/flex/mx"
  	xmlns:s="library://ns.adobe.com/flex/spark">
    <fx:Style>
        @namespace s "library://ns.adobe.com/flex/spark";
        @namespace mx "library://ns.adobe.com/flex/mx";
        s|Group {
            color: #FFCC33;
        }
    </fx:Style>
    <s:VGroup>
        <s:Button label="This Button is in a VGroup and its label is yellow."/>
        <s:Label text="This Label is in a VGroup and its text is yellow."/>
    </s:VGroup>
    <s:Button label="This Button is not in a VGroup, but it is still yellow."/>
    <s:Label text="This Label is not in a VGroup, but it is still yellow."/>
</s:Application>
```

## Global selector

The `global` selector lets you apply styles to all controls. Because the `global` selector is like a type selector, you do not preface its definition with a period in CSS.

```css
global {
    fontSize: 22;
    textDecoration: underline;
}
```

## Font Faces

`@font-face` declarations are used to embed a font in the application.

After you embed a font with an `@font-face` declaration, you can use the value of the `fontFamily` property, or **alias**,
in a selector’s property declarations.

**Syntax**

```
@font-face {
    src: url("location");
    fontFamily: alias;
    [fontStyle: normal | italic | oblique] ;
    [fontWeight: normal | bold | heavy] ;
    [embedAsCFF: true | false] ;
    [advancedAntiAliasing: true | false];
}
```

### Properties

#### src

Specifies the file path location of a font. In Flex 4 and later, you cannot embed
a font by its local name only. 

If you specify a relative location, the location is relative to the file in which the
`@font-face` rule appears.

`src` may consist of either an `url(...)` call or a `local(...)` call. Using `local(...)` will lookup a system font name.

`src` may appear more than one time.

#### fontFamily

Sets the alias for the font that you use to apply the font in style sheets. This
property is required.

If you embed a font with a family name that matches the family name of a
system font, the Flex compiler gives you a warning. You can disable this
warning by setting the `show-shadows-system-font-warnings` compiler
option to `false`.

#### fontStyle

Set the style type face value for the font.

This property is optional, unless you are embedding a face that requires it.
The default value is `normal`. Valid values are `normal`, `italic`, and `oblique`.

#### fontWeight

Set the weight type face value for the font.

This property is optional, unless you are embedding a face that requires it.
The default value is `normal`. Valid values are `normal`, `bold`, and `heavy`.

#### embedAsCFF

Indicates whether to embed an FTE-enabled font for components. Flash Text
Engine (FTE) is a library that provides text controls with a rich set of formatting
options.

For Flex 4 and later, the default value is `true`. If you set the `compatibility-version` compiler option to 3.0.0, then the default value is `false`.

If you set the `embedAsCFF` property to `true`, then you can use the advanced
formatting features of FTE such as bidirectional text, kerning, and ligatures. If
you set the value of `embedAsCFF` to false, then the embedded font does not
support FTE, and works only with the MX text components.

#### advancedAntiAliasing

Determines whether to include the advanced anti-aliasing information when
embedding the font.

This property is optional and only used for legacy fonts. This property is ignored
if you embed a font with the `embedAsCFF` property set to `true`.

You cannot use this option when embedding fonts from a SWF file because this
option requires access to the original, raw font file to pre-calculate anti-aliasing
information at compile time.

## Embed()

The `Embed(...)` function call takes a form equivalent to the ActionScript 3 `[Embed]` meta-data.

```css
.style1 {
    backgroundImage: Embed("../assets/butterfly.gif");
    backgroundAlpha: .2;
}
```

## Function Calls

The following function calls are supported:

```css
url(...)
url(...) format(...)

local(...)

ClassReference(...)
PropertyReference(...)
```

### ClassReference()

* `ClassReference(null)` results into the `null` value.
* `ClassReference("full.ClassName")` resolves to the class `ClassName` in the `full` package.

### PropertyReference()

`PropertyReference(...)` refers to a property in the enclosing Flex component.

## Selector Combinators

Only descendant selector combinators are currently supported in Flex.

```css
.myStyleName1 s|Label {
    color: green;
}
```

## Conditions

### Class condition

```css
s|Label.className
```

### ID condition

```css
s#idValue
```

### Pseudo condition

```css
s:loadingState
```

### Pseudo element condition

```css
s::loadingState
```

### Not condition

```css
s|Panel:not(:first-child)
```

### Attribute condition

```css
s|Label[loadingState]
```

## Style value formats

Style properties can be of types String or Number. They can also be Arrays of these types. In addition to a type, style
properties also have a format (`Length`, `Time`, or `Color`) that describes the valid values of the property. Some properties
appear to be of type Boolean (taking a value of true or false), but these are Strings that are interpreted as Boolean
values. This section describes these formats.

### Length format

The `Length` format applies to any style property that takes a size value, such as the size of a font (or `fontSize`).
`Length` is of type Number.

The `Length` type has the following syntax:

```plain
length[length_unit]
```

The following example defines the `fontSize` property with a value of 20 pixels:

```css
.myFontStlye {
    fontSize: 20px;
}
```

If you do not specify an unit, the unit is assumed to be pixels. The following example defines two styles with the same font size:

```css
.myFontStlye {
    fontSize: 20px;
}

.myOtherFontStlye {
    fontSize: 20;
}
```

*Note: spaces are not allowed between the length value and the unit.*

The following table describes the supported `length` units:

| Unit | Scale | Description |
| ---- | ----- | ----------- |
| px | Relative | Pixels. |
| in | Absolute | Inches. |
| cm | Absolute | Centimeters. |
| mm | Absolute | Millimeters. |
| pt | Absolute | Points. |
| pc | Absolute | Picas. |

*Note: the numeric values specified for font size in Flex are actual character sizes in the chosen units. These values are not
equivalent to the relative font size specified in HTML using the `<font>` tag.*

Flex does not support the `em` and `ex` units. You can convert these to `px` units by using the following scales:

* 1em = 10.06667px
* 1ex = 6px

In Flex, all lengths are converted to pixels prior to being displayed. In this conversion, Flex assumes that an inch equals
72 pixels. All other lengths are based on that assumption. For example, 1 cm is equal to 1/2.54 of an inch. To get the
number of pixels in 1 cm, multiply 1 by 72, and divide by 2.54.

When you use inline styles, Flex ignores units and uses pixels as the default.

The `fontSize` style property allows a set of keywords in addition to numbered units. You can use the following
keywords when setting the `fontSize` style property. The exact sizes are defined by the client browser:

* `xx-small`
* `x-small`
* `small`
* `medium`
* `large`
* `x-large`
* `xx-large`

The following example class selector defines the `fontSize` as `x-small`:

```css
.smallFont {
    fontFamily: Arial, Helvetica, "_sans";
    fontSize: x-small;
}
```

### Time format

You use the `Time` format for component properties that move or have built-in effects, such as the `ComboBox`
component when it drops down and pops up. The `Time` format is of type Number and is represented in milliseconds.
Do not specify the units when entering a value in the `Time` format.

The following example sets the `openDuration` style property of the `myTree` control to 1000 milliseconds. The default
value is 0, so this example opens the tree nodes considerably more slowly than normal.

```xml
<?xml version="1.0"?>
<s:Application
    xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:mx="library://ns.adobe.com/flex/mx"
    xmlns:s="library://ns.adobe.com/flex/spark"
    creationComplete="initApp()">
    <fx:Script><![CDATA[
        public function initApp():void {
            myTree.setStyle("openDuration", 1000);
            myTree.setStyle("paddingLeft", 50);
        }
        ]]>
    </fx:Script>
    <fx:Declarations>
        <fx:XMLList id="treeData">
            <node label="Mail Box">
                <node label="Inbox">
                    <node label="Marketing"/>
                    <node label="Product Management"/>
                    <node label="Personal"/>
                </node>
                <node label="Outbox">
                    <node label="Professional"/>
                    <node label="Personal"/>
                </node>
                <node label="Spam"/>
                <node label="Sent"/>
            </node>
        </fx:XMLList>
    </fx:Declarations>
    <mx:Panel title="Tree Control Example" width="100%">
        <mx:Tree id="myTree" width="100%" labelField="@label" dataProvider="{treeData}"/>
    </mx:Panel>
</s:Application>
```

### Color format

You define `Color` in several formats. You can use most of the formats only in the CSS style definitions. The following
table describes the recognized `Color` formats for a style property:

<table>
<tr>
<th>Format</th>
<th>Description</th>
</tr>
<tr>
<td>hexadecimal</td>
<td>

Hexadecimal colors are represented by a three-digit code or six-digit code preceded by a pound sign (`#`) in CSS, such as `#FFF` or `#FFFFFF` for the white color.

</td>
</tr>
<tr>
<td>RGB</td>
<td>

RGB colors are a mixture of the colors red, green, and blue, and are represented in percentages of the color’s
saturation. The format for setting RGB colors is `color: rgb(x%, y%, z%)`, where the first value is the percentage of
red saturation, the second value is the percentage of green saturation, and the third value is the percentage of blue
saturation.

You can use the RGB format only in style sheet definitions.

</td>
</tr>
<tr>
<td>8-bit octet RGB</td>
<td>

The 8-bit octet RGB colors are red, green, and blue values from 0 to 255. The format of 8-bit colors is `rgb([0-255], [0-255], [0-255])`.

You can use the 8-bit octet RGB format only in style sheet definitions.

</td>
</tr>
<tr>
<td>keywords</td>
<td>

Several standard [CSS color keywords](https://www.w3.org/wiki/CSS/Properties/color/keywords) are available,
such as `Aqua`, `Black`, `Blue`, `Fuchsia`, `Gray`, `Green`, `Lime`, `Maroon`, `Navy`, `Olive`, `Purple`, `Red`, `Silver`, `Teal`, `White`,
`Yellow`.

You can use the CSS keyword format in style sheet definitions and inline style declarations.

Keywords are not case-sensitive. 

</td>
</tr>
</table>

Color formats are of type Number. When you specify a format such as a keyword, Flex converts that String to
a Number.

CSS style definitions and the <fx:Style> tag support the following color value formats:

```css
.myStyle {
    themeColor: #6666CC; /* CSS hexadecimal format */
    color: Blue;         /* CSS keyword */
}
```

You can use the following color value formats when setting the styles inline or using the `setStyle()` method:

```xml
<?xml version="1.0"?>
<s:Application
    xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:mx="library://ns.adobe.com/flex/mx"
    xmlns:s="library://ns.adobe.com/flex/spark"
    creationComplete="initApp()">
    <fx:Script><![CDATA[
        public function initApp():void {
            styleManager.getStyleDeclaration("spark.components.Button").setStyle("color","Blue");
        }
        public function changeStyles(e:Event):void {
            // Check against "255" here, because that is the numeric value of "Blue".
            if (e.currentTarget.getStyle("color") == 255) {
                e.currentTarget.setStyle("color", "Red");
            } else {
                e.currentTarget.setStyle("color", "Blue");
            }
        }
    ]]></fx:Script>
    <s:Button id="myButton" label="Click Here" click="changeStyles(event)"/>
</s:Application>
```

## Media Queries

Flex includes partial support for CSS media queries. In Flex, media queries let you conditionally apply styles based on
the DPI and OS of the target device. You typically use this feature if you are developing for mobile or tablet devices
that have different target DPIs. For example, if a tablet has a DPI of 300, then you can set the font size to one value. If
a tablet has a DPI of 200, then you can set the font size to a different value.

Media queries use the values of the `application-dpi` and `os-platform` CSS properties to determine which styles to
apply. 

The syntax for using media queries is as follows:

```plain
@media [media_type] [application-dpi: 180|240|320] [and|not|only]
[os-platform: "Android"|"IOS"|"Macintosh"|"Windows"|"Linux"]
```

The only supported value for the `media_type` property is `screen`. As a result, you do not need to specify the media type.

If you do not specify a value for the `application-dpi` or `os-platform` properties, then all are assumed. You can
specify one or more resolutions or platforms by comma-separating their values.

The following example changes the font size and color based on the value of the `applicationDPI` property:

```xml
<?xml version="1.0" encoding="utf-8"?>
<s:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:s="library://ns.adobe.com/flex/spark"
    applicationDPI="320"
    creationComplete="initApp()">
    <fx:Style>
        @namespace s "library://ns.adobe.com/flex/spark";
        @namespace mx "library://ns.adobe.com/flex/mx";
        s|TextArea {
            fontSize: 12;
        }
        @media (application-dpi: 160) and (os-platform: "Windows"), (os-platform: "Macintosh"), (os-platform: "Linux") {
            s|TextArea {
                fontSize: 12;
                color: red;
            }
        }
        @media (application-dpi: 240) and (os-platform: "Windows"), (os-platform: "Macintosh"), (os-platform: "Linux") {
            s|TextArea {
                fontSize: 18;
                color: green;
            }
        }
        @media (application-dpi: 320) and (os-platform: "Windows"), (os-platform: "Macintosh"), (os-platform: "Linux") {
            s|TextArea {
                fontSize: 24;
                color: blue;
            }
        }
    </fx:Style>
    <fx:Script>
        private function initApp():void {
            myTextArea.text = "OS: " + Capabilities.os + "\n"
                + "MFR: " + Capabilities.manufacturer + "\n"
                + "DPI: " + applicationDPI;
        }
    </fx:Script>
    <s:TextArea id="myTextArea" width="100%"/>
</s:Application>
```
