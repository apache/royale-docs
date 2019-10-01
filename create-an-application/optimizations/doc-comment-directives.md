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
title: Doc-Comment Directives
---
## (Optimization options)  
# Doc-Comment Directives  


Warning:  This document is a work-in-progress/undergoing review.  


These settings are actionscript code level settings. They are implemented in the form of instructions to the compiler based on doc-comment tags, frequently as annotations against members of classes.
They are always in the format 
 **@royale{name here}**
 
They have no case variation (all lower case, not camel case, for example) and may have arguments that follow after some white space. They are fully expressed on a single line, and a newline terminates them.
 

|[Suppress Warnings](create-an-application/optimizations/doc-comment-directives.html#suppress-warnings)  |[@royalesuppresspublicvarwarning](create-an-application/optimizations/doc-comment-directives.html#royalesuppresspublicvarwarning)   |
|[Output Optimizations](create-an-application/optimizations/doc-comment-directives.html#output-optimizations)  |[@royaleigorecoercion](create-an-application/optimizations/doc-comment-directives.html#royaleigorecoercion)   |
| |[@royalesuppressresolveuncertain](create-an-application/optimizations/doc-comment-directives.html#royalesuppressresolveuncertain)  | 
| |[@royalesuppresscompleximplicitcoercion](create-an-application/optimizations/doc-comment-directives.html#royalesuppresscompleximplicitcoercion)  | 
| |[@royalesuppressvectorindexcheck](create-an-application/optimizations/doc-comment-directives.html#royalesuppressvectorindexcheck)  | 
|[Miscellaneous](create-an-application/optimizations/doc-comment-directives.html#miscellaneous)  |[@royalesuppressexport](create-an-application/optimizations/doc-comment-directives.html#royalesuppressexport)   |
| |[@royalesuppressclosure](create-an-application/optimizations/doc-comment-directives.html#royalesuppressclosure)  | 


* * *
## Todo
The following are placeholders/reminders for future content while this document is being worked on:
>@royaleignoreimport  
>@royaledebug  
>@royalenoimplicitstringconversion  

* * *
## Suppress Warnings  

### @royalesuppresspublicvarwarning {#royalesuppresspublicvarwarning}  
This is used to suppress warning output by the compiler.

public variables are not protected from renaming optimizations by javascript in a way that permits them to continue to be accessible via dynamic access.
This means that for:

class MyThing{  
	public var myImportantVar:String = 'myValue';  
}
```as3
var myThing:MyThing = new MyThing();
var s:String = myThing.myImportantVar; //this always works
var fieldName:String = 'myImportantVar';
s = myThing[fieldName]; //this will work in a js-debug build, but may not work in js-release
```
Because of issues like the above, the Royale compiler outputs a warning to alert the developer.
However in many cases, the dynamic access may not be needed, and using a public var will be fine.
To prevent the warning from the compiler, the doc comment directive can be used as follows:
```as3
/**
* @royalesuppresspublicvarwarning
*/
public var myImportantVar:String = 'myValue';
```
* * *
## Output Optimizations

### @royaleigorecoercion type {#royaleigorecoercion} 

Used for: performance tuning, code size tuning.  
This is an option to avoid compiler output of coercions of a certain type.  
It can help avoid unnecessary code and improve performance.

A simplistic, illustrative example is:
```as3
if (myVar is MyClass) { //this generates code to check if myVar is of type 'MyClass'
	(myVar as MyClass).myClassMethod(); 
	//the above normally generates similar code to check if myVar is of type 'MyClass'
	//or a subclass of MyClass, and if it is not, treats it as null
	MyClass(myVar).myOtherClassMethod(); 
	//the above normally generates similar code to check if myVar is of type 'MyClass'
	//or a subclass of MyClass, and if it is not, throws an error
}
```
In both the above examples, the outer conditional `myVar is MyClass` check already assures us that myVar resolves to 'MyClass' as a type.  
So the extra overhead of code that performs `myVar as MyClass` or `MyClass(myVar)` coercions is redundant, because we can already be sure it will resolve successfully.  
If the definition of MyClass is in a package called mypackage, then its **fully qualified name** is mypackage.MyClass.  
The following can then be used to avoid the redundant (as described above) javascript output code:
```
/**
* @royaleigorecoercion mypackage.MyClass
* /
```  

* * *

### @royalesuppressresolveuncertain optional_arg {#royalesuppressresolveuncertain} 

Used for: performance tuning, code size tuning.  
This is a local variation for controlling specificity of the corresponding compiler configuration setting '-js-resolve-uncertain'.  
Please read the [Strict equality comparisons](create-an-application/optimizations/compiler-configuration-settings.html#strict-equality-comparisons) section of [Compiler Configuration Settings](create-an-application/optimizations/compiler-configuration-settings.html) for general information about this setting.


How to use:  
A simplistic example is:
```as3
/**
* setting goes here
*/
public function testResolveUncertain():void{
	var myClass:Class = int;
	if (new myClass(30) === 30) trace('it worked!);
	var myOtherClass:Class = String;
	if (new myOtherClass('test') === 'test') trace('it worked again!);
}
```
In the above example, both of 'new myClass(30)' and 'new myOtherClass('test')' will have extra code to cover the cases where variations occur in javascript.

**@royalesuppressresolveuncertain false**  

Using the above setting, if the compiler configuration setting is -js-resolve-uncertain=false, then the above annotation will override that locally to turn it on (true). 
This only affects the code scope of the annnotated method definition.

**@royalesuppressresolveuncertain true**  
or simply:  
**@royalesuppressresolveuncertain**  
Both of the above settings will be the same as '-js-resolve-uncertain=false' for the annotated method's code scope.

**@royalesuppressresolveuncertain myClass**  
Using the above setting, if the compiler configuration setting is -js-resolve-uncertain=true, then the above annotation will override that locally to turn it off (false) only for the myClass Class variable and not for the myOtherClass Class variable. 


* * * 

### @royalesuppressvectorindexcheck optional_arg {#royalesuppressvectorindexcheck} 

Used for: performance tuning, code size tuning.  
This is a local variation for controlling specificity of the corresponding configuration setting '-js-vector-index-checks'.  

Please read the [Vector Index Checking](create-an-application/optimizations/compiler-configuration-settings.html#vector-index-checking) section of [Compiler Configuration Settings](create-an-application/optimizations/compiler-configuration-settings.html) for general information about this setting.

How to use:
A simplistic example is:  
```as3
/**
* setting goes here
*/
public function myTest():void{
	var vi:Vector.<int> = new <int>[0, 1, 2, 3, 4];
	vi[8] = 0; 
	//index 8 above is too high
	//by default this will throw a RangeError, but if 
	//@royalesuppressvectorindexcheck is used to suppress index checking,
	//no runtime error would be thrown in javascript.
}
```

**@royalesuppressvectorindexcheck false**

In the above case, if the compiler configuration setting is *-js-vector-index-checks=false*, then the above annotation will override that locally to turn it on (true). 
This only affects the code scope of the annnotated method definition.

**@royalesuppressvectorindexcheck true**  
or simply:   
**@royalesuppressvectorindexcheck**

Both of the above settings will be the same as '-js-vector-index-checks=false' for the annotated method's code scope.

**@royalesuppressvectorindexcheck vi**

In the above case, the effect is as if there was a '-js-vector-index-checks=false' setting applied specifically to any Vector with a variable name of 'vi'


* * *  

### @royalesuppresscompleximplicitcoercion optional_arg {#royalesuppresscompleximplicitcoercion} 

Used for: performance tuning, code size tuning.  
This is a local variation for controlling specificity of the corresponding configuration setting '-js-complex-implicit-coercions'.  
Please read the [Implict Coercions of non-primitive types](create-an-application/optimizations/compiler-configuration-settings.html#implicit-complex-coercions) section in [Compiler Configuration Settings](create-an-application/optimizations/compiler-configuration-settings.html) for general information about this setting if you have not already done so.  
How to use:

A simplistic example is:
```as3
/**
* setting goes here
*/
public function testComplexImplicitCoercion():void{
	var something:* = new Cat();
	var myDog:Dog = something;
}
```
In the above example, the default output will have extra code generated in javascript, that would be similar in actionscript to:  
`var myDog:Dog = Dog(something);`

**@royalesuppresscompleximplicitcoercion false**

Using the above setting, if the compiler configuration setting is -js-complex-implicit-coercions=false, then the above annotation will override that locally to turn it on (true).  
This only affects the code scope of the annnotated method definition.  

**@royalesuppresscompleximplicitcoercion true**  
or simply:  
**@royalesuppresscompleximplicitcoercion**   
Both of the above settings will be the same as '-js-complex-implicit-coercions=false' for the annotated method's code scope.  

**@royalesuppresscompleximplicitcoercion Dog**  
Note that in this example, Dog is a top level class (top level package). Otherwise it needs the fully qualified class name.  
Using the above setting, if the compiler configuration setting is -js-complex-implicit-coercions=true, then the above annotation will override that locally to turn it off (false) only for the implicit coercions involving the Dog class.  
As another example, if the definition of Dog is in a package called myanimals, then its fully qualified name is myanimals.Dog, and it should be expressed as follows:  
**@royalesuppresscompleximplicitcoercion myanimals.Dog**

  

* * *
## Miscellaneous  

The following are intended mainly for use by framework developers, but are documented here for completeness. In most cases these are not recommended for use in applications.
They may be helpful in specific cases *when used with caution* for library development.
 
### @royalesuppressexport {#royalesuppressexport}  
The above is used to prevent a public class member from having an exported setting in the release build.
This can be used with classes that are used to emulate certain as3 language features in javascript, and often are intended only for output generated by the compiler and not used directly by a developer.
It has the effect to making the annotated class member 'pay as you go' because if the compiler does not generate output that uses it, the code and any dependencies that are specific to it are eliminated from the release build output.
They can also be used as another way to offer opt-in features, for a type of PAYG approach that works in regular actionscrip, and which could also be then supported in code via a bead for use in mxml.
An example of this is the ExtraData class in the Reflection library, which has static methods to add opt-in support for additional reflection data.
 
### @royalesuppressclosure {#royalesuppressclosure} 
The above is used to suppress closure generation inside a method scope of a class member.
This breaks normal as3 behavior in the javascript output, and is only rarely needed in cases where there is an advantage to use it to generate javascript that treats the ***this*** reference differently in the generated code.
An example of its usage is in the default Vector emulation code for javascript.
Recommendation: use with caution and test extensively.