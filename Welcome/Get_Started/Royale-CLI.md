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
#Royale CLI


As I was trying to write a `Setting up Royale with npm `blog post, I
realized that things could be much easier for npm users.  So, I built the
Royale CLI tool.  It takes inspiration from the create-react-app and the
angular cli projects.

Here are the details:

*To Install: *
npm install @apache-royale/royale-js -g
npm install @apache-royale/cli -g

After installation:

*Help *
royale help

*Setup *
royale new  my-royale-app
cd my-royale-app

 This creates a simple app: my-royale-app/src/Main.mxml


*Run in debug mode *
royale serve:debug

 Compiles the project in debug mode
 Compiles with source map option
 Starts a http server and serves the files from the bin/js-debug directory
 Opens the default browser and navigates to http://localhost:3000
 Listens to src folder
 When any file changes, it will recompile the app
 Automatically reloads the browser to show the updated application

*Run in release mode *
royale serve:release

 Compiles the project in release mode
 Starts a http server and serves the files from the bin/js-release
directory
 Opens the default browser and navigates to http://localhost:3001
