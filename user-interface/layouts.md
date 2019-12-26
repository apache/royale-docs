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
title: Layouts
description: Visual screen organization for your components
permalink: /user-interface/layouts
---
# Layouts

Visual screen organization for your components

Laying out components in Royale works a bit differently than in the Adobe or Apache Flex SDKs. If you don’t care about the _why_ and want to get to the _how_, skip ahead to the “Royale Layouts" section.

The traditional Flex SDKs used a three-phase, optionally frame-delayed, validation mechanism. Two phases were top-down; one phase was bottom up. The idea was to handle any change anywhere. Also percentages were defined as a percentage of the non-fixed area of the container. Just about every object that didn’t have explicit widths and heights got measured because measurements helped define the minimum sizes for things with percentage widths and heights.

This system worked well, but with some annoying issues:

*  Folks were often surprised that things didn’t shrink as expected because of the minimum size calculation for things with percentage sizes
*  You could get into “invalidation/validation loops” where the size of things would compute to be different on each layout pass
*  Time was spent measuring things and often those measurements weren’t used
*  Time was spent setting up event listeners for changes that never got used

Royale works with the browser in which it is running:

*  Browsers do not have frame mechanisms or timelines. If you change the display property for a component in your UI, the change shows up right away.
*  Browsers and CSS calculate percentages as a simple calculation on the parent's size.


## Royale Layouts

When managing layouts, Royale recognizes three scenarios:

1. The parent sizes the child
2. The content sizes the component it is in
3. the developer or the application sets explicit height and width for the component

If the component has an explicitly set width but not height or vice versa, the component falls into scenario 1 or 2 based on whether the unspecified dimension has a percentage set on it.

Another, more subtle principle, is that _width is slightly more important than height_. That’s the way browsers seem to work, so if a choice has to be made, the layout will try to determine the width before the height.

Unlike the traditional Flex SDKs, a percentage in Royale is a strict percentage of the parent’s size. Royale makes no attempt to figure out what things can be shrunk or stretched. This saves having to loop through the children twice: once to figure out how much room there is, and a second time to shrink or stretch things.

Another difference is that, in Royale, a parent does not watch its children’s display properties for changes. If the height and/or width of some child object changes, the parent and its parents may not refresh their layout. You may have to dispatch a “layoutNeeded” event or use an MXML tag to cause a “layoutNeeded” event to dispatch. If we start to see common scenarios where everyone is setting up these update events, we may build in somehow the ability for parents to monitor changes in their childrens' sizes. For example, the Image and ImageButton components force a layout in their parents when the image content arrives, since that is a common pattern.

This fits with Royale's  “just-in-time” instead of “just-in-case” philosophy. In the dozens of containers and components available in the Royale component sets, only three require “layoutNeeded” events.

### When Royale lays out a component

* Components that don’t have any percentage or explicit dimensions, including width and height CSS styles, or both ”left" and “right" CSS styles, or both “top” and “bottom” CSS styles are considered to be in category 2 and sized when the set of children changes. When setting up from MXML, all of the children are added, then a single _childrenAdded_ event is dispatched to kick off the layout. When you use AS APIs, the _childrenAdded_ event is dispatched as children are added. You can suppress the event if you are changing lots of children if you remember to dispatch the event yourself when done.
* Children that have both an explicitly set width and height are laid out when the children are added.
* All other children theoretically have at least one dimension that is relative to the parent’s size. 

At the beginning of the application, the default Application class sets the initial view to the size of the Flash Player or browser window. This generally causes a single top-down pass through all of the children that weren’t already sized to content or sized explicitly. When that pass done, if a dimension is sized to content, the layout sets the size of that dimension.

### Layout Guidelines

_ActionScript vs JavaScript_
When creating your own layout, take advantage of the platforms' abilities. Keep in mind that the ActionScript version of a layout mimics what you can do with HTML. The VerticalLayout, for example, just sets the HTML elements that support the FlexJS components to have a display style of 'block' so they appear on separate lines. 

The ActionScript version of a layout may be more complex since it has to do more work. The ActionScript version of VerticalLayout is more complex and provides a really good example of how to write a layout.

You may be able to create layouts which can be cross-compiled from ActionScript to JavaScript, but you may get better performance if you write native JavaScript layouts.

### Composition

Layouts work with the container classes (Group, View, Container, DataContainer, List) and the chart classes. A container has an area called the "contentView" where the items go that are being laid out. The contentView is different depending on the platform (HTML, Flash) and the type of container. For Group, the contentView is always itself, while for Container, the contentView is specific to the platform. On the HTML platform, the contentView is almost always the same as the component since DIV can do much of the work. 

On the Flash platform, the contentView is managed by a Viewport which is responsible for the size and position of the contentView. If a Container is being scrolled, a ScrollableViewport is used instead of the plain Viewport; in the browser/HTML, scrolling is done by the DIV simply by adding "overflow:auto" to its style sheet.

### Sizing

As mentioned above, containers may be sized explicitly or by their content. This can happen in either or both dimensions (for example, a container that specifies a width and not a height). When a container is being sized by its content, the layout is used to determine the container's size by calculating a bounding box that surrounds the children once the layout has been run. 

Some layouts need to know the amount of space they have to work with. The contentView can provide that through its width and height properties. When a container is being sized by its content, the layout may not get valid width and/or height values from the contentView. In this case, the layout must assume the container is infinitely wide or tall or the layout can make some assumptions and impose its own constraints.

Layouts such as VerticalLayout and HorizontalLayout do not depend on the container having a size. These layouts simply follow an algorithm to position the children, which makes them ideal candidates for containers whose size must be determined by the content.

### Padding and Margin

The layout handles offsets introduced by padding and margin styles. On the HTML platform, the DIV (along with CSS) handles padding, margins, and borders. The SWF implementation of a layout has to account for these things and handle them appropriately.

If you look at the ActionScript version of VerticalLayout, you'll see how padding and margin values are obtained from the components and used to calculate the placement of the items in the layout. Your layout may need to do the same thing if it is to respect padding and margin when your application is run from Flash.

### Custom Container Views

Using a container as a base for a new component is often a good idea if you want to take advantage of layouts. In Royale, the container's _view bead_ handles the majority of the work. For Containers, this is the ContainerView bead (for Group it is the GroupView bead). Unless your component needs special handling for scrolling you can extend Group and GroupView for your view bead. 

Use a layout to arrange the sub-elements of your component. If you need to, write a custom layout to handle special cases such as elements that should not be included in the layout ("chrome" elements).

Your custom view bead may also need to override some protected functions which are called during the layout process:

* beforeLayout() is called just prior to the layout running. You can use this function to eliminate elements from the layout process by setting their visible property to false (you can reset them later). 
* afterLayout() is called after the layout has run and sized and positioned the elements. Make sure you call _super.afterLayout()_ so the container can be sized by its content if it does not have a fixed size. This is especially important if you are extending ContainerView as this is where the scrolling viewport is set for the SWF platform.

### Custom Content

On the Flash platform, the Container class uses a simple component, ContainerContentArea, for the contentView that holds the elements to be displayed and arranged by the layout. The Royale framework automatically adds any elements specified in MXML to the contentView. If your component needs to generate, or programmatically fill, the content of a container, you may want to consider creating a custom contentView.

The List and chart components are examples of doing this. The List extends Container, but it also provides a special contentView called DataGroup, which is designed to work with item renderers. The List then uses the VerticalLayout to present the item renderer instances.

The chart components use ChartDataGroup which is designed to work with the graphic elements of the chart; charts use their own layouts to make each chart type.

To replace a Container's content view:

* Create the custom content view by extending _org.apache.flex.html.supportClasses.ContainerContentArea_. 
* Add the functions you need to create the content.
* In the CSS Style definition for your class, add IContentView with a ClassReference that names your custom content view.

## Examples

[Tour de Jewel](https://royale.apache.org/tourdejewel){:target='_blank'} is a suite of examples of the effects you can get with Apache Royale. It features our Jewel component set. There are seven examples of layouts, with sample code you can download, study, and adapt to your project.
