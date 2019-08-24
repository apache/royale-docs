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
---

# Strands and Beads

Adding functionality to a component through composition

Strands and beads are key concepts in Royale, related to the [PAYG](welcome/features/payg.html)  (pay as you go) concept. The idea is to keep component code as lightweight as possible, and to add functionality and complexity only to the components that need it.

> For example, you may use a lot of text input fields in your application, but only one or two need to be able to protect passwords by converting the display of text the user provides into dots. You may want to disable or enable some components, but not all of them, while an end user is working with your application. There is no reason to have that extra functionality (and added weight of code) available everywhere _"just in case"_, as was the rule in Apache Flex.

Every component contains the minimum code necessary to perform its basic functions, and has _"strands"_ onto which you can string _"beads"_ of functionality that let the component do what you want it to do in a particular place in your application. 

## Finding the beads you need

Finding the beads we provide per component or know what beads are available (at least in the official Apache Royale SDK) can be a daunting task, since can be hundreds of this little pieces of code distributed all over the framework code. For this reason this documentation is trying to help in that task providing a list of beads in each component page, so users can refer to a concrete _"strand"_ (the component) and see a list of recommended _"beads"_. Normally you can have:

* __Specific Component Beads__. (beads only usable for a concrete component like the [Jewel PasswordInput](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/PasswordInput){:target='_blank'} for a [Jewel TextInput](component-sets/jewel/jewel-textinput.html))
* __Common Shared Beads__. Beads that can be used by more than one strand like [Jewel Disabled bead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'} can be used by [Jewel Button](component-sets/jewel/jewel-button.html), [Jewel TextInput](component-sets/jewel/jewel-textinput.html) or [Jewel CheckBox](component-sets/jewel/jewel-checkbox.html) controls for example.

## Adding a bead

There are three ways of adding beads to a component: baked into the code using `<j:beads>`, through CSS, and dynamically using `addBead()`.

### Adding a bead directly in the code

Each _strand_ support a `beads` array and users can add beads in MXML.

In the following example we are using the [Jewel TextInput](component-sets/jewel/jewel-textinput.html) strand to add a [Jewel TextPrompt](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls.textinput/TextPrompt){:target='_blank'} and [Jewel Disabled](https://royale.apache.org/asdoc/index.html#!org.apache.royale.jewel.beads.controls/Disabled){:target='_blank'} beads to the strand. Notice that while `TextPrompt` is specific to TextInput, `Disabled` can be used by many other Jewel components.

```mxml
<j:TextInput text="Disabled with text...">
    <j:beads>
        <j:TextPrompt prompt="Disabled TextInput..."/>
        <j:Disabled/>
    </j:beads>
</j:TextInput>
```

### Adding a bead through CSS

Adding beads through [Cascading Style Sheets (CSS)](https://en.wikipedia.org/wiki/Cascading_Style_Sheets){:target='_blank'} is easy. You declare __CSS__ rules where the the _selector_ is the strand and the declaration block is composed by one or more delarations. Declarations can be _bead declarations_ or _standard CSS declarations_ separated by semicolons.

A bead declaration is composed of the bead type as the __property__ part (i.e, [IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'}, [IBeadModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadModel){:target='_blank'}, [IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'}, ...) and a a `ClassReference` of the bead we want to assign as the __value__ part.

The following example shows a bead declaration:

```css
IBeadView: ClassReference("org.apache.royale.jewel.beads.views.ListView");
```

In the example we want to assign a `org.apache.royale.jewel.beads.views.ListView` as the bead view (`IBeadView`) of the component strand.

Notice that Royale use __CSS__ to configure components with defaults beads. The following
code snippet is the default initial bead configuration for a [Jewel List](component-sets/jewel/jewel-list.html) and is declared though [SASS](https://sass-lang.com){:target='_blank'} (that will be compiled to __CSS__). 

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

Thanks to __CSS__, Royale developers can override default beads through its own coded __CSS__ files, that will take priority over framework __CSS__ rules, or through AS3 and/or MXML code.

### Adding a bead dynamically using addBead()

Other way to add a bead is though __ActionScript__ using the `addBead` API method.

Lets see an example code:

```as3
// for Jewel Alert component, retrieve the AlertView (IBeadView) 
var alertView:AlertView = alert.getBeadByType(IBeadView) as AlertView;

// create a VerticalLayout (IBeadLayout)
var verticalLayout:VerticalLayout = new VerticalLayout();
verticalLayout.gap = 9;

// add the bead layout to the content part of the view layout
alertView.content.addBead(verticalLayout);
```
See a full example of the code above in the [Customization through the Royale API](https://royale.apache.org/customization-through-the-royale-api/){:target='_blank'} example.

## Creating a bead

The following piece of code reveals the most basic bead structure to use when coding a bead:

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

All beads implement [IBead](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBead){:target='_blank'} interface (or a subclass like [IBeadModel](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadModel){:target='_blank'} or [IBeadView](https://royale.apache.org/asdoc/index.html#!org.apache.royale.core/IBeadView){:target='_blank'}) and can refer to the strand component using the `strand` method implementation of the IBead interface.

Beads use to be tiny pieces of code so in this way we get a great encapsulation of functionality with few lines of code. 

If you see a need for a bead that does not yet exist, you can create your own and [contribute it to the Royale project](https://royale.apache.org/get-involved/){:target='_blank'}. Information on the bead lifecycle is available at [Creating Components](https://cwiki.apache.org/confluence/display/FLEX/Creating+Components).

## Strand management

_Adding and removing beads; the significance of bead order_
