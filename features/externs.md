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
title: Externs
description: Use external javascript libraries in ActiopnScript
permalink: /features/externs
---

# Externs

Use external JavaScript libraries in ActionScript

Some [Apache Royale](https://royale.apache.org/) elements have limited cross-browser support at the moment. To get reliable display and performance in those cases, Royale makes use of existing external JavaScript libraries. For example, [Jewel Alert](https://apache.github.io/royale-docs/component-sets/jewel/alert) uses the HTML dialog element, which is not reliable across all browsers. So Jewel Alert references the _dialogPolyfill_ external library to make sure the display is as intended in whichever browser the alert displays.

[Google Closure Compiler (GCC)](https://developers.google.com/closure/compiler){:target='_blank'} provides a mechanism called _@externs_ that Apache Royale uses to declare that a name for a class, property or function is defined in external code and so should not be renamed when application code is compiled.

The compiler assumes that externs will exist in the environment in which the compiled JavaScript will be interpreted.

Jewel Alert invokes _dialogPolyfill_, which is an AS3 class with _@externs_ in its comments. That informs GCC that this class has the same name as the external JavaScript library it references, and is not to be renamed in the compile process. Apache Royale can use the properties of the external library, and you can even see them as options if you are using an IDE, with _code completion_ and _code intelligence_ enabled.

This is the code of the AS3 dialogPolyfill.as class file:

```as3
////////////////////////////////////////////////////////////////////////////////
//
//  Licensed to the Apache Software Foundation (ASF) under one or more
//  contributor license agreements.  See the NOTICE file distributed with
//  this work for additional information regarding copyright ownership.
//  The ASF licenses this file to You under the Apache License, Version 2.0
//  (the "License"); you may not use this file except in compliance with
//  the License.  You may obtain a copy of the License at
//
//      http://www.apache.org/licenses/LICENSE-2.0
//
//  Unless required by applicable law or agreed to in writing, software
//  distributed under the License is distributed on an "AS IS" BASIS,
//  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
//  See the License for the specific language governing permissions and
//  limitations under the License.
//
////////////////////////////////////////////////////////////////////////////////
package
{
    /**
     * @externs
     */
    COMPILE::JS
    public class dialogPolyfill
    {
        /** 
         * <inject_html>
         * <script src="https://cdnjs.cloudflare.com/ajax/libs/dialog-polyfill/0.4.9/dialog-polyfill.min.js"></script>
         * <link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/dialog-polyfill/0.4.9/dialog-polyfill.min.css">
         * </inject_html>
         */
        public function dialogPolyfill(){}
         
        public static function registerDialog(dialog:Element):void {}
    }
}
```

As you can see you normaly has:

* A __class level__ `@externs` comment.
* A __constructor__ `<inject_html>` that holds the external javascript libraries that should be injected in your main application `index.html`.
* The __signatures__ of the methods you want to expose in AS3.

Then you will be able to call `registerDialog` method in the following way:

```as3
    COMPILE::JS
    {
    dialogPolyfill.registerDialog(dialog);
    }
```

To learn more about using the huge range of external JavaScript libraries that is available, see [Using external JavaScript libraries in Apache Royale](https://royale.apache.org/using-external-javascript-libraries-in-apache-royale/){:target='_blank'}.

## ExternalInterface

Check [ExternalInterface](features/external-interface) to learn another way to communicate to/from external JavaScript libraries.
