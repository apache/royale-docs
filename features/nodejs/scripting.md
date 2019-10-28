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
title: Command line scripting
description: Write a Node.js script with ActionScript and Apache Royale
permalink: /features/nodejs/scripting
---

# Node.js scripting with Apache Royale

Write command line scripts for Node.js using ActionScript

Much of the JavaScript development ecosystem is powered by [Node.js](https://nodejs.org/). This runtime is used for simple command line scripts, web servers, and more. With the help of Apache Royale, developers can use [ActionScript](features/as3) to create their own tools that run on Node.js.

## Hello, Node.js

Create a file named *MyServer.as*, and add the following code:

```actionscript
package
{
	public class MyServer
	{
		public function MyServer()
		{
		}
	}
}
```

Apache Royale requires an ActionScript class, like this one, as the entrypoint for a Node.js project. The constructor will run automatically on startup.

Next, let's expand this code to create a simple server using the [http](https://nodejs.org/api/http.html) module, which is included with Node.js.

```actionscript
package
{
	import http.IncomingMessage;
	import http.Server;
	import http.ServerResponse;

	public class MyServer
	{
		private static const HOSTNAME:String = "localhost";
		private static const PORT:int = 3000;

		public function MyServer()
		{
			var server:Server = http.createServer(handleRequest);

			server.listen(PORT, HOSTNAME, handleServerStart);
		}

		private function handleRequest(req:IncomingMessage, res:ServerResponse):void
		{
			res.statusCode = 200;
			res.setHeader("Content-Type", "text/plain");
			res.end("Hello World\n");
		}

		private function handleServerStart():void
		{
			console.log("Server running at http://" + HOSTNAME + ":" + PORT + "/");
		}
	}
}
```

> Notice that there's no need to call `require("http")`, as would be necessary in plain JavaScript. When the Apache Royale compiler detects a reference to a Node.js module, like `http`, it automatically generates the appropriate `require()` calls.

## Compile with asnodec

Using Apache Royale's **asnodec** compiler, compile the project into JavaScript code that can be run with Node.js:

```sh
asnodec src/MyServer.as
```

The generated JavaScript code will be created in the *bin/js-debug* folder for debug builds, and the *bin/js-release* folder for release builds.

## Run the project

> To run the generated JavaScript, you must have [Node.js](https://nodejs.org/) installed.

Use the following command to run the compiled project:

```sh
node bin/js-release/index.js
```

In a web browser, open **http://localhost:3000/** and verify that you can see a webpage that simply contains the text, "Hello World".