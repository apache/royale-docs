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
title: Royale CLI
---
# Royale CLI
Royale CLI is a command-line tool that makes creating and compiling applications easier for users of <a href="https://www.npmjs.com/" target="_blank">npm</a>, the JavaScript package manager.

## Installing Royale CLI

If you have not installed Royale already, use this command in the command window:
```
npm install @apache-royale/royale-js -g
```
Then run:
```
npm install @apache-royale/cli -g
```

## Working with Royale CLI
For information at any time aabout available commands and options, run:
```
royale help
```

### Creating a new application
Navigate in the command window to the directory where you want to create the new application, called here "my-royale-app", then run:
```
royale new  my-royale-app
```
This creates a new directory structure using the name of the application, and creates a basic app with one main file: my-royale-app/src/Main.mxml.

To review the app structure so far, navigate into the new direcctory:
```
cd my-royale-app
```

### Running your application
Navigate in the command window into your application's directory.

To compile and run in **debug mode**, run:
```
royale serve:debug
```
Royale:
  - Compiles the project in debug mode, with a source map option.
  - Starts a http server and serves the files from the bin/js-debug directory.
  - Opens the default browser and navigates to http://localhost:3000.
  - Listens to the *src* folder. When any file changes, Royale will recompile the app and reload the browser to show the updated application.
  
To compile and run in **release mode**, run:
```
royale serve:release
```
Royale:
  - Compiles the project in release mode.
  - Starts a http server and serves the files from the bin/js-release
directory.
  - Opens the default browser and navigates to http://localhost:3001.
