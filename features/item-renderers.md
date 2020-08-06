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
title: ItemRenderers
description: Visual representation of data items in lists and other collection components
permalink: /features/item-renderers
---

# ItemRenderers

Visual representation of data items in lists and other collection components

Collections of data are composed by objects or items. Several components in Royale can show collections of data to the user like _List_, _DataGrid_, _TabBar_ or _ButtonBar_. Those components need to describe each item and adapt the visaluzation to the data inside each object. Apache Royale uses Item Renderers components along with the before mentioned collection components to realize the visualization of each piece of data stored in each collection object.

# Inline

Although Item Renders use to be declared in a separate file (and this is the recommended way), you can also declare an item renderer inline for convenience:

´´´mxml
<j:DataContainer width="100%" labelField="name" dataProvider="{dataList}">
    <j:beads>
        <j:Viewport clipContent="false"/>
    </j:beads>
    <j:itemRenderer>
        <fx:Component>
            <j:ListItemRenderer width="100%">
                <fx:Script>
                    <![CDATA[            
                    import vos.Provider;

                    [Bindable("dataChange")]
                    public function get provider():Provider {
                        return data as Provider;
                    }      
                    ]]>
                </fx:Script>
                <j:beads>
                    <js:ItemRendererDataBinding/>
                </j:beads>
                <j:HGroup gap="3" itemsVerticalAlign="itemsCenter">
                    <js:FontAwesomeIcon text="{FontAwesome5IconType.PARKING_CIRCLE}" 
                                        faStyle="{FontAwesomeIcon.REGULAR}" 
                                        relativeSize="{FontAwesomeIcon.SIZE_LG}"
                                        style="color: {provider.color};"/>
                    <j:Label text="Offered by" className="weight-bold"/>
                    <j:Image width="60" height="24" src="{provider.logo}">
                        <j:beads>
                            <js:ErrorImage emptyIsError="true"/>
                        </j:beads>
                    </j:Image>
                </j:HGroup>
            </j:ListItemRenderer>
        </fx:Component>
    </j:itemRenderer>
</j:DataContainer>
´´´

## Examples

- [Using an item renderer with a list](https://royale.apache.org/using-an-item-renderer-with-a-list){:target='_blank'}
