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
title: Download Royale
---

# Download Royale

You can download Apache Royale via Node Package Manager (NPM) or from mirrors of Apache releases.  NPM is simpler.

## NPM

To use NPM to install Royale, use the following command line for your operating system.

### Mac

```
sudo npm install @apache-royale/royale-js -g
```
### Windows

```
npm install @apache-royale/royale-js -g
```

If you want SWF output as well as JavaScript output, install these packages instead.

### Mac

```
sudo npm install @apache-royale/royale-js-swf -g
```
### Windows

```
npm install @apache-royale/royale-js-swf -g
```

If the install completes successfully, you are ready to compile your application with Royale by using the mxmlcnpm tool from the command-line.  The NPM install should have put mxmlcnpm in your path.

## Apache Mirrors

Use the following links to get a choice of mirrors to use for your download.

[tar.gz (for Mac)](http://www.apache.org/dyn/closer.lua/royale/0.9.1/binaries/apache-royale-0.9.1-bin-js.tar.gz){:target='_blank'}

[zip (for Windows)](http://www.apache.org/dyn/closer.lua/royale/0.9.1/binaries/apache-royale-0.9.1-bin-js.zip){:target='_blank'}


If you want SWF output as well as JavaScript output, download one of these packages instead.

[tar.gz (for Mac)](http://www.apache.org/dyn/closer.lua/royale/0.9.1/binaries/apache-royale-0.9.1-bin-js-swf.tar.gz){:target='_blank'}

[zip (for Windows)](http://www.apache.org/dyn/closer.lua/royale/0.9.1/binaries/apache-royale-0.9.1-bin-js-swf.zip){:target='_blank'}

Once downloaded, uncompress the file into a folder somewhere.  This folder will be referred to as the SDK folder throughout the documentation.  If you chose the package with SWF support, you will need to follow the instructions in the README to install libraries from Adobe System Inc or use the Apache Ant script InstallAdobeSDKs.xml by running from the SDK folder:

```
ant -f InstallAdobeSDKs.xml
```

At this point, you should be able to run the js/bin/mxmlc compiler from your Royale SDK folder to compile a Royale application.  See the [Hello World](Welcome/Get_Started/Hello-World.html) section for more details.
