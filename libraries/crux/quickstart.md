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
title: Quick Start
description: Quick Start with Crux
permalink: /libraries/crux/quickstart
---

# Crux Quick Start

Learn Crux in just six steps

Page Contents:

* [A Lightning Look at Configuration](libraries/crux/quickstart.html#configuration)
* [The "Big Three": Dependency Injection, Event Handling, and Server Interaction](libraries/crux/quickstart.html#the-big-three)
* [Adding Dependency Injection](libraries/crux/quickstart.html#dependency-injection)
* [Dispatching and Handling Events](libraries/crux/quickstart.html#dispatching-handling-events)
* [Talking to the Server](libraries/crux/quickstart.html#talking-to-server)
* [There's More Where That Came From](libraries/crux/quickstart.html#more)

> You can download this Quick Start from GiHub. It's available in the Royale Crux Examples repository on GitHub, along with more examples. Check it [here](https://github.com/apache/royale-asjs/tree/develop/examples/crux/CruxQuickStart){:target='_blank'}

## A Lightning Look at Configuration {#configuration}

Configuring Crux in your Royale application is very straightforward: declare Crux, define the beanProviders and config properties, and optionally define one or more loggingTargets to view debugging messages. Here is an example:

```mxml
<j:Application xmlns:fx="http://ns.adobe.com/mxml/2009"
               xmlns:j="library://ns.apache.org/royale/jewel"
               xmlns:js="library://ns.apache.org/royale/basic"
               xmlns:crux="library://ns.apache.org/royale/crux"
               xmlns:view="crux.quickstart.view.*"
               xmlns:config="crux.quickstart.config.*"
               initialize="setUp()">
    <fx:Script>
        <![CDATA[
        public function setUp():void {
            tracer('application setUp stub');
        }
        ]]>
    </fx:Script>

    <j:beads>
        <!-- support for simulated stage events in javascript (needed for Crux view processing)-->
        <crux:JSStageEvents packageExclusionFilter="_default_"/>
        <!-- BeanProviders simply contain the non-display objects that Crux should process. -->
        <crux:Crux>
            <crux:beanProviders>
                <config:Beans/>
            </crux:beanProviders>

            <crux:config>
            <!-- eventPackages value tells Crux the path to your Event classes, viewPackages is an optional value that speeds up processing of display classes. -->
                <crux:CruxConfig
                    eventPackages="crux.quickstart.event.*"
                    viewPackages="crux.quickstart.view.*"/>
            </crux:config>
        </crux:Crux>
    </j:beads>

    <j:valuesImpl>
        <js:SimpleCSSValuesImpl />
    </j:valuesImpl>

    <j:initialView>
            <j:View>
                <view:UserForm id="userForm" />
            </j:View>
     </j:initialView>
</j:Application>
```

Non-visual components that you want Crux to manage are defined in a BeanProvider tag. Any beans that you define within the BeanProvider are processed by Crux for dependency injection and the creation of event handlers. In the following example, a `UserService` and a `UserController` are created:

```mxml
<crux:BeanProvider
    xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:crux="library://ns.apache.org/royale/crux"
    xmlns:service="crux.quickstart.service.*"
    xmlns:controller="crux.quickstart.controller.*">
    
    <service:UserService id="userService"/>
    <controller:UserController id="userController"/>
    
</crux:BeanProvider>
```

## The "Big Three": Dependency Injection, Event Handling, and Server Interaction {#the-big-three}

The three most commonly used features of Crux are its dependency injection capabilities, its event handling features, and its server interaction utilities. Let's look at how each of these work.

## Adding Dependency Injection {#dependency-injection}

Dependencies are injected by using `[Inject]` metadata. In this example, the `UserService` is injected into the `UserController`:

```as3
package crux.quickstart.controller
{
    import crux.quickstart.model.User;
    import crux.quickstart.service.UserService;
     
    public class UserController
    {  
        [Inject]
        public var userService : UserService;  
         
        [Bindable]
        public var currentUser : User;
    }
}
```

In addition to injecting a bean, you can inject individual bean properties. In this example, the `currentUser` property of the `UserController` is injected into a `UserForm` visual component. Note that it is not necessary for the `UserForm` to be declared as a bean in the `BeanProviders` tag. When visual components are added to the display list, Crux automatically inspects them and processes any metadata tags that are found.

```mxml
<j:GridCell xmlns:fx="http://ns.adobe.com/mxml/2009"
    xmlns:j="library://ns.apache.org/royale/jewel"
    xmlns:js="library://ns.apache.org/royale/basic"
    desktopNumerator="1" desktopDenominator="2"
    tabletNumerator="1" tabletDenominator="2"
    phoneNumerator="1" phoneDenominator="1">

    <j:beads>
        <js:ContainerDataBinding/>
    </j:beads>

    <fx:Script>
    <![CDATA[
        import crux.quickstart.event.UserEvent;
        import crux.quickstart.model.User;

        [Bindable]
        /**
         * We could inject the whole controller instance, but we only need
         * one property from the controller, the current user, so we just
         * inject that property.
         * Using setter style binding below instead of direct property binding
         * Injection here (for variety in example)
         */
        public var user : User;

        //example of setter style binding Injection
        [Inject( source = "userController.currentUser", bind = "true" )]
        public function setUser(val:User):void {
            this.user = val;
        }
    ]]>
    </fx:Script>
    
    <j:Form>
        <j:FormHeading label="User Form (Crux Quickstart Example)"/>
        <j:FormItem label="User ID: ">
            <j:Label localId="userId" text="{isNaN( user.id ) ? 'N/A' : user.id}" />
        </j:FormItem>
        <j:FormItem label="First Name: ">
            <j:TextInput id="firstName" text="{user.firstName}" />
        </j:FormItem>
        <j:FormItem label="Last Name: ">
            <j:TextInput id="lastName" text="{user.lastName}" />
        </j:FormItem>
        <j:FormItem label="Email: ">
            <j:TextInput id="email" text="{user.email}" />
        </j:FormItem>
        <j:FormItem>
            <j:Button text="Save" emphasis="primary"  click="saveUser()" />
        </j:FormItem>
    </j:Form>
</j:GridCell>
```

## Dispatching and Handling Events {#dispatching-handling-events}

When using Crux, you dispatch standard Royale events. In this example, we've expanded the `UserForm` to create and dispatch an event when the form button is clicked. Crux listens for events being dispatched within the display list and handles them automatically. We add to the `UserForm` the `saveUSer()` method as follows.

```mxml
    /**
     * Handle the user hitting the save button. We capture the form data
     * and dispatch a standard Royale event. No Crux-specific events or
     * special central dispatcher needed!
     */
    private function saveUser() : void
    {
        user.firstName = firstName.text;
        user.lastName = lastName.text;
        user.email = email.text;
        var event : UserEvent = new UserEvent( UserEvent.SAVE_USER_REQUESTED );
        event.user = user;
        dispatchEvent( event );
    }
```

A look at the `UserEvent` confirms that this is just a simple, standard event. The only thing to note here is that the event has **bubbles set to true**. This allows the event to bubble up the display list so that it can be handled by Crux:

```as3
package crux.quickstart.event
{
    import crux.quickstart.model.User;
    import org.apache.royale.events.Event;

    public class UserEvent extends Event
    {
        public static const SAVE_USER_REQUESTED : String = "saveUser";
        public var user : User;
        
        /**
         * This is just a normal Royale event which will be dispatched from a view
         * instance. The only thing to note is that we set 'bubbles' to true, so 
         * that the event will bubble up the 'display' list, allowing Crux to listen
         * for your events.
         */ 
        public function UserEvent( type:String )
        {
            super( type, true );
        }
    }
}
```

We've seen how to dispatch events from the display list, but how do we handle the events? Crux provides a `[EventHandler]` metadata tag to do this. In the example below, we have expanded the `UserController` to add an event handler method. In this case, when Crux encounters an event of type `UserEvent.SAVE_USER_REQUESTED`, it will automatically invoke the `saveUser()`method in the `UserController`. By specifying a value of `user` for the properties attribute, Crux will locate the _user_ property in the `UserEvent` and pass this as a parameter to the handler method:

```as3
    /**
     * [PostConstruct] methods are invoked after all dependencies are injected.
     * In this example, we set up a default user after the bean is created.
     */ 
    [PostConstruct]
    public function createDefaultUser() : void {
        currentUser = new User();
    }

    /**
     * Perform a server request to save the user
     */ 
    [EventHandler( event="UserEvent.SAVE_USER_REQUESTED", properties="user" )]
    public function saveUser( user : User ) : void {
        // TODO: Add server interaction
    }   
```

One last feature to note regarding event dispatching. We've seen how an event dispatched from the display list will bubble up until it is processed by Crux. But what about dispatching events from non-visual components like controllers and services? Crux offers the `[Dispatcher]` metadata tag to meet this need. In the `UserService` shown below, Crux will automatically inject an event dispatcher into the dispatcher property. Any events dispatched though this dispatcher will also be processed by Crux and trigger any event handler methods associated with the event:

```as3
package crux.quickstart.service
{
    import crux.quickstart.model.User;

    import mx.rpc.AsyncToken;

    import org.apache.royale.crux.utils.services.MockDelegateHelper;
    import org.apache.royale.events.IEventDispatcher;

    public class UserService
    {
        /**
         * The [Dispatcher] metadata tag instructs Crux to inject an event dispatcher.
         * Event's dispatched via this dispatcher can trigger event mediators.
         */ 
        [Dispatcher]
        public var dispatcher : IEventDispatcher;
        
        /**
         * To avoid a live server dependency, we use a Crux
         * helper class to let us create fake AsyncTokens
         */ 
        private var mockHelper : MockDelegateHelper;
        
        public function UserService()
        {
            mockHelper = new MockDelegateHelper();
        }
        
        /**
         * In a real app, we'd invoke a RemoteObject, HTTPService, etc.
         * For this simple example, we'll set a random ID on the returned User
         * to simulate the process of saving a User.
         */ 
        public function saveUser( user : User ) : AsyncToken
        {
            user = user.clone();//clone it to simulate a different object being returned from the server
            user.id = Math.round( Math.random() * 100 );
            return mockHelper.createMockResult( user );
        }
    }
}
```

## Talking to the Server {#talking-to-server}

Our `UserController` can now respond when a save user event is dispatched. The final piece of the puzzle is having the application make a call to the server to actually save the user in a database. Typically, Royale requires you to manually create `Responder` objects to attach to `AsyncTokens` that will handle `ResultEvent` and `FaultEvent`. Crux offers some helpful features to sidestep these manual processes. Below, you see the final version of our `UserController`. Because it has the Crux helper object `ServiceHelper` injected, we can use its `executeServiceCall()` method. This method will automatically obtain the `AsyncToken` for the __RPC__ call and create `Responder` objects. In this case, we call `userService.saveUser()`, and specify `handleSaveUserResult` to handle the successful response from the server. Although it is not shown here, we can also specify a method to use as the fault handler.

```as3
    /**
     * Perform a server request to save the user
     */ 
    [EventHandler( event="UserEvent.SAVE_USER_REQUESTED", properties="user" )]
    public function saveUser( user : User ) : void {
        serviceHelper.executeServiceCall(userService.saveUser( user ), handleSaveUserResult);
    }

    /**
     * Handle the server call result
     */
    private function handleSaveUserResult( event : ResultEvent ) : void
    {
        // Show an Alert just to make it obvious that the save was successful.
        currentUser = event.result as User;

        // Show an Alert just to make it obvious that the save was successful.
        Alert.show( 'User saved successfully! id:' + currentUser.id, 'Success' );
    }
```

## There's More Where That Came From {#more}

This quick tour has shown how easy it is to configure Crux and use its core features. But Crux offers much more than this! Please read the User Guide, Best Practices, and Advanced Topics to learn more.