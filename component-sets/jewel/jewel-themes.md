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
title: Jewel Themes
---

# Jewel Themes

The look and feel of the component set

Jewel UI Set focus themes. Themes provides the capability of change the appearance of _all_ components at once. 
A theme is a predefined CSS file (and optionally a other assets like images) that holds the definitions of each Jewel component and its subcomponents a long the default beads used to configure that components. 

Royale use the theme to add the right css selectors to the final compilation so when the user loads the application the required css and other files are loaded and the application shows a concrete look and feel.

Jewel comes with predefined themes based on the 12 color wheel below:

![Jewel 12 color wheel](assets/images/apache-royale-jewel-12-color-wheel.jpeg)

Jewel has been designed to cover multiple visual needs and support Light/Dark and Flat/No Flat themes:

![Light/No Flat](assets/images/apache-royale-jewel-light-noflat.jpeg){:height="80%" width="80%"}
<br>
Light/No Flat
<br><br>
![Dark/No Flat](assets/images/apache-royale-jewel-dark-noflat.jpeg){:height="80%" width="80%"}
<br>
Dark/No Flat
<br><br>
![Light/Flat](assets/images/apache-royale-jewel-light-flat.jpeg){:height="80%" width="80%"}
<br>
Light/Flat
<br><br>
![Dark/Flat](assets/images/apache-royale-jewel-dark-flat.jpeg){:height="80%" width="80%"}
<br>
Dark/Flat
<br><br>

Jewel Themes are mostly a CSS with all needed CSS rules predefined. We create this CSSs using the Jewel SASS Theme framework located in JewelTheme project. So updating rules in this theme, we can recompile all themes to update it with the latest changes.