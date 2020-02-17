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
title: Configuration
description: Crux Configuration
permalink: /libraries/crux/configuration
---

# Crux Configuration

Learn how to configure Crux

Page Contents:

* [Configuration Overview](libraries/crux/configuration.html#overview)
<!-- * [Logging] -->
<!-- * [setUpEventType, setUpEventPhase](libraries/crux/configuration.html#setup-event)
* [tearDownEventType, tearDownEventPhase](libraries/crux/configuration.html#tear-down) -->
* [Default Dispatcher](libraries/crux/configuration.html#default-dispatcher)

## Configuration Overview {#overview}

You configure each Crux instance using the `CruxConfig` class. It allows you to modify common settings, and to provide values that allow your tags and code elsewhere to be more concise. Below is an example with all properties shown. Where applicable, they have been set to their default values. However, in most cases, the default values should work fine (see the note below on Configuration Defaults).

```mxml
<crux:Crux>
    <crux:beanProviders>
        <local:MyBeans/>
    </crux:beanProviders>
 
    <crux:config>
        <crux:CruxConfig
            eventPackages="com.foo.event.*, org.bar.event.*"
            viewPackages="com.foo.view.*, org.bar.view.*"
            defaultFaultHandler="handleUnhandledFaults"
            defaultDispatcher="global" />
    </crux:config>
</crux:Crux>
```

> **Configuration Defaults**. Unless you are specifying your own set up and tear down values, the only configuration values that commonly need to be set are `eventPackages` and `viewPackages`. If you are using Crux's support for server communication, you may also set `defaultFaultHandler`.

> **Specifying Packages**. Note that due to limitations in the _AS3_ reflection API, when you define `eventPackages`, you must specify each package individually. Children of your specified packages cannot be resolved and must be explicitly set. This limitation does not apply to `viewPackages` because they are handled differently, but for consistency it may be useful to use the same rules to define both sets of packages.

<!-- ## Logging

As you can see above, Crux includes a basic logging target called SwizTraceTarget to trace debugging information to the console. Due to the way the MXMLC compiler works, it was not possible to use the built-in Royale logging target(s), because it increases the size of the Crux swc by an unacceptable amount. If necessary, you can extend the AbstractSwizLoggingTarget to customize the output. -->

<!-- ## setUpEventType, setUpEventPhase {#setup-event}

These properties configure the listener that Crux will use to trigger the set up of views (assuming they are eligible) to inject dependencies, create event handlers, etc. The default is a capture phase listener (to catch all views regardless of their place in the display list hierarchy) for the `Event.ADDED_TO_STAGE` event. -->
<!-- , with a priority of 50.  -->

<!-- ## tearDownEventType, tearDownEventPhase {#tear-down}

These properties configure the listener that Crux will use to trigger the tearing down of views to clean up injected dependencies, remove event handlers, etc. The default is a capture phase listener for the `Event.REMOVED_FROM_STAGE` event. -->
<!-- , with a priority of 50. -->

## Default Dispatcher {#default-dispatcher}

The default dispatcher value is "global". This means that in the case where a Crux instance is the child of another Crux instance, the child will use the parent dispatcher. This allows for easy communication between Crux instances, since they all share the same event dispatcher. However, if you want to force a child Crux to use it's own dispatcher, you can set this value to "local". In most cases, developers should not need to change the default value ("global"). More information on parent-child Crux instances can be found in the section on [Module support](libraries/crux/module-support).
