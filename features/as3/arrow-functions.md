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
title: Arrow functions
description: Arrow function expressions in ActionScript
permalink: /features/as3/arrow-functions
---

# Arrow function expressions in ActionScript

-allow-arrow-functions

[Apache Royale](https://royale.apache.org/){:target='_blank'} adds support for arrow function expressions in [ActionScript](features/as3). An arrow function provides shorter syntax for declaring local functions, and it inherits the `this` value from its containing scope.

Arrow functions do not have names. Unlike regular function expressions, arrow functions omit the `function` keyword, and they have an arrow (in the format `=>`) between the parameters and the body instead. In certain situations, both the parentheses around the parameters and the braces around the body may be omitted.

_Requires Apache Royale 0.9.13 or newer._

## Compiler option

Royale enables arrow functions by default. To disable arrow functions in your application, use the `-allow-arrow-functions` compiler option.

```sh
mxmlc -allow-arrow-functions=false MyApp.mxml
```

## Code examples

A simple, traditional function expression might be defined like this:

```as3
var func:Function = function(name:String):String
{
    return "Hello, " + name;
}
```

One may replace it with an arrow function expression with equivalent
behavior, but shorter syntax:

```as3
var func:Function = (name:String) => "Hello, " + name;
```

The arrow function expression above has the following differences in syntax:

- Arrow functions do not start with a `function` keyword. Instead, they include an arrow (`=>`) symbol between the signature and the body.
- When the body of an arrow function contains a single expression, the `{}` braces are considered optional and may be omitted.
- If the braces are omitted, the result of the single expression in the body is automatically returned. In fact, one is not allowed to use the `return` keyword when the braces are omitted.
- If the braces are omitted, the return type does not need to be declared. The compiler can automatically infer a return type from the single expression in the body.

Omitting parts of an arrow function is optional, but some may prefer to include the braces, the return type, and the `return` keyword.

```as3
var func:Function = (name:String):String => {
    return "Hello, " + name;
}
```

If an arrow function has a single parameter, the parentheses around that parameter become optional when the parameter is simply an identifier, with no declared type and no default value. However, omitting the type of the parameter will result in a compiler warning, and the type will default to `*`, so it is not recommended.

```as3
var func:Function = name => "Hello, " + name;
// Warning: return value for function has no type declaration.
```

### Using `this` in arrow functions

When a function object is created within a method, and it needs to access the value of `this`, using an arrow function expression can lead to simpler code.

```as3
class MyClass {
    public function createCallback():Function {
        return () => this;
    }
}
```

In comparison, using a regular function expression is more verbose because `this` from the outer scope needs to be saved in a local variable:

```as3
class MyClass {
    public function createCallback():Function {
        var self:MyClass = this;
        return function():MyClass {
            return self;
        }
    }
}
```

Attempting to use `this` directly in the function object would return the global object instead of an instance of `MyClass`.

## Limitations of arrow functions in Royale

Other ActionScript compilers, such as the one in the [Apache Flex SDK](https://flex.apache.org/){:target='_blank'}, may not recognize arrow functions. Attemping to pass ActionScript or MXML source code that contain arrow functions to another compiler may result in compile-time errors. In other words, to write 100% portable ActionScript code that works with any compiler, avoid using arrow functions and any of Royale's other [extensions to the ActionScript language](features/as3#new-actionscript-language-features-in-royale).
