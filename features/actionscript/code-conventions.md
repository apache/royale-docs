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
title: Code Conventions
description: Coding standards for writing code in ActionScript 3
permalink: /features/as3/code-conventions
---

# Code Conventions

Coding standards for writing code in ActionScript 3

*Warning:  This document is not complete.*

## Packages

Packages have lower.case.names separated by periods if needed. Names using mixedCase (starting with lower case) are ok, but short package names are preferred so that you aren't tempted to mixCase.

## Classes

Classes have MixedCase names starting with a capital letter (and no hyphens).

## Constants

Constants have CAPITALIZED_NAMES with words separated by underscores '_'.

## Properties

Properties have mixedCase names starting with a lower case letter.

## Events

Events have mixedCase names starting with a lower case letter.

## Event Classes

While Apache Flex had lots of event classes, Royale strives to have as few as possible since each class has download overhead. Royale has an Event which has an event name in the "type" field and no other payload. A ValueEvent contains one item that might be of interest to the listener. ValueChangeEvent has oldValue/newValue. There may be a StringEvent and other 'typed' event classes.

Event constants go in the class that will dispatch the event. Thus the developer only has to import one class and write the code that uses it.

The reason behind this change is partly that JavaScript runtimes don't really type-check event instances. Royale has code that will do the type-checking, but it is pretty rare to have to discriminate between event classes. So it is best to turn off type-checking code in Royale.

To compare:

### Flex

```as3
public class TimerEvent {
  public const TIMER:String = "timer";
}

public class Timer {
   dispatchEvent(new TimerEvent(TimerEvent.TIMER));
}
```

Usage:

```as3
import TimerEvent;
import Timer;

var timer:Timer = new Timer();
timer.addEventListener(TimerEvent.TIMER, timerHandler);

function timerHandler(event:TimerEvent):void
{
}
```

### Royale

```as3
public class Timer {
   public const TIMER:String = "timer";
   dispatchEvent(new Event(TIMER));
}
```

Usage:

```as3
import Timer;

var timer:Timer = new Timer();
timer.addEventListener(Timer.TIMER, timerHandler);

function timerHandler(event:Event):void
{
}
```
