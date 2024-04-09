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
title: Strands and Beads
description: Adding functionality to a component through composition
permalink: /features/strands-and-beads
---

# Strands and Beads

Adding functionality to a component through composition

Strands and beads are key concepts in [Apache Royale](https://royale.apache.org/), related to the [PAYG](features/payg)  (pay as you go) concept. The idea is to keep component code as lightweight as possible, and to add functionality and complexity only to the components that need it.

{:align="center"}
![Fig 1: MVC with Strands and Beads](assets/images/strand-beads/strand-bead-1.jpg){:height="70%" width="70%"}

In the image, a [TextInput](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html/TextInput){:target='_blank'} is composed by a model ([TextModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads.models/TextModel){:target='_blank'}), a view ([TextInputWithBorderView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads/TextInputWithBorderView){:target='_blank'}) and a controller ([EditableTextKeyboardController](https://royale.apache.org/asdoc/index.html#!org.apache.royale.html.beads.controllers/EditableTextKeyboardController){:target='_blank'}). These are the minimun [MVC](https://en.wikipedia.org/wiki/Model–view–controller){:target='_blank'} beads to make it work for this component.

> For example, you may use a lot of text input fields in your application, but only one or two need to be able to protect passwords by converting the display of text the user provides into dots. You may want to disable or enable some instances of the text input component, but not all of them, while an end user is working with your application. There is no reason to have that extra functionality (and added weight of code) available everywhere _"just in case"_, as was the rule in Apache Flex.

{:align="center"}
![Fig 1: Adding optional Beads to the Strand](assets/images/strand-beads/strand-bead-2.jpg){:height="70%" width="70%"}

In the image we are composing (adding) two optional beads to the strand.

Every Royale component contains the minimum code necessary to perform its basic functions, and has _"strands"_ onto which you can string _"beads"_ of functionality that let an instance of the component do what you want it to do in a particular place in your application.

## Finding the beads you need

Finding the beads that will provide what you want for a given component, or even knowing what beads are available in the official Apache Royale SDK can be a daunting task. There are hundreds of these little pieces of code distributed all over the framework code. For this reason we are gradually assembling a list of beads on each component page, so users can refer to a concrete _strand_ (the component) and see a list of _beads_ that work with it. Normally you can have:

* __Specific Component Beads__. (beads only usable for a specific component, like [Jewel PasswordInput](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/PasswordInput){:target='_blank'} for an instance of [Jewel TextInput](component-sets/jewel/textinput))
* __Common Shared Beads__. Beads that can be used with more than one component, like [Jewel Disabled bead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'}, which can be used by [Jewel Button](component-sets/jewel/button), [Jewel TextInput](component-sets/jewel/textinput) or [Jewel CheckBox](component-sets/jewel/checkbox).

## Adding a bead

There are three ways to add beads to a component: bake it into the code using `<j:beads>`, declare it through CSS, or add it dynamically using `addBead()`.

### Adding a bead directly in the code

Each _strand_ supports a `beads` array and users can add beads in MXML.

In the following example we are using the [Jewel TextInput](component-sets/jewel/textinput) strand to add [Jewel TextPrompt](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/TextPrompt){:target='_blank'} and [Jewel Disabled](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'} beads to the strand. Note that while `TextPrompt` is specific to TextInput, you can use `Disabled` with many Jewel components.

```mxml
<j:TextInput text="Disabled with text...">
    <j:beads>
        <j:TextPrompt prompt="Disabled TextInput..."/>
        <j:Disabled/>
    </j:beads>
</j:TextInput>
```

### Adding a bead through CSS

Adding beads through [Cascading Style Sheets (CSS)](https://en.wikipedia.org/wiki/Cascading_Style_Sheets){:target='_blank'} is easy. You declare CSS rules where the _selector_ is the strand and the declaration block has one or more delarations. Declarations can be _bead declarations_ or _standard CSS declarations_ separated by semicolons.

A bead declaration has the bead type as the __property__ part (for instance, [IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'}, [IBeadModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadModel){:target='_blank'}, and [IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'}) and a `ClassReference` to the bead we want to assign as the __value__ part.

Here is an example of a CSS bead declaration. We assign `org.apache.royale.jewel.beads.views.ListView` as the bead view (`IBeadView`) of the component strand:

```css
IBeadView: ClassReference("org.apache.royale.jewel.beads.views.ListView");
```

Royale uses __CSS__ to configure components with defaults beads. The following
code snippet is the default initial bead configuration for a [Jewel List](component-sets/jewel/list) and is declared though [SASS](https://sass-lang.com){:target='_blank'} (that gets compiled to __CSS__). 

```sass
j|List
    IBeadView:  ClassReference("org.apache.royale.jewel.beads.views.ListView")
    IBeadController: ClassReference("org.apache.royale.jewel.beads.controllers.ListSingleSelectionMouseController")
    IBeadLayout: ClassReference("org.apache.royale.jewel.beads.layouts.VerticalLayout")
    IItemRendererClassFactory: ClassReference("org.apache.royale.core.ItemRendererClassFactory")
    IItemRenderer: ClassReference("org.apache.royale.jewel.itemRenderers.ListItemRenderer")
    IViewport: ClassReference("org.apache.royale.jewel.supportClasses.scrollbar.ScrollingViewport")
    IViewportModel: ClassReference("org.apache.royale.html.beads.models.ViewportModel")
    IBeadModel: ClassReference("org.apache.royale.jewel.beads.models.ArrayListSelectionModel")
    IDataProviderItemRendererMapper: ClassReference("org.apache.royale.jewel.beads.itemRenderers.DataItemRendererFactoryForCollectionView")
```

Royale developers can override default beads through their own coded CSS files that will take priority over framework CSS rules, or through AS3 and/or MXML code.

### Adding a bead dynamically with addBead()

The third way to add a bead is though __ActionScript__ using the `addBead()` API method.

Here is example code:

```as3
// for the Jewel Alert component, retrieve the AlertView (IBeadView) 
var alertView:AlertView = alert.getBeadByType(IBeadView) as AlertView;

// create a VerticalLayout (IBeadLayout)
var verticalLayout:VerticalLayout = new VerticalLayout();
verticalLayout.gap = 9;

// add the bead layout to the content part of the view layout
alertView.content.addBead(verticalLayout);
```
See a full example of the code above in the [Customization through the Royale API](https://royale.apache.org/customization-through-the-royale-api/){:target='_blank'} example.

### Accessing a bead from a strand
There are many cases where you need to find a specific bead without necessarily knowing the implementation. The two most common cases are accessing a strand's view and model.

For these two cases, any class which implements `IStrandWithModelAndView` or inherits from `UIBase` (which is pretty much every visual component) has direct access to the `view` and `model` getters on the strand. These getters should always be used for views and models. 

Sometimes, a component might have more than one model and you might not be sure if the one you want is the main one. In that case you should use the `getModelByType(strand,classOrInterface)` function in the `org.apache.royale.html.util` package. It will find the correct bead in the most efficient way it can.

For other bead types, you can use `strand.getBeadByType(classOrInterface)`. It will find the bead you need from the beads which belong to the strand. You can use this for views although it's less efficient than accessing the view directly. You _should not_ use this for models because models are only loaded the first time they are accessed and if you use `strand.getBeadByType(IBeadModel)` you will get null if the model has not yet been accessed.

## Creating a bead

The following piece of code shows the most basic bead structure to use when you create a bead:

```as3
package beads
{	
	import org.apache.royale.core.IBead;
	import org.apache.royale.core.IStrand;
	import org.apache.royale.core.UIBase;
	
	/**
	 *  sample code for a bead class
	 */
	public class SomeBead implements IBead
	{
		protected var _strand:IStrand;
		
		/**
		 *  @copy org.apache.royale.core.IBead#strand
		 *  
		 *  @royaleignorecoercion org.apache.royale.core.UIBase;
		 */
		public function set strand(value:IStrand):void
		{
			_strand = value;

			// do something
		}
	}
}
```

All beads implement the [IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} interface (or a subclass like [IBeadModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadModel){:target='_blank'} or [IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'}) and can refer to the strand component using the `strand` method implementation of the IBead interface.

Beads can be tiny pieces of code so in this way we get great encapsulation of functionality with a few lines of code. 

If you see the need for a bead that does not yet exist, you can create your own and [contribute it to the Royale project](https://royale.apache.org/get-involved/){:target='_blank'}. Information on the bead lifecycle is available at [Creating Components](https://cwiki.apache.org/confluence/display/FLEX/Creating+Components).

## Strand management

_This section will include information on adding and removing beads and the significance of bead order_
