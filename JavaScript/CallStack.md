_[General](../README.md) > [JavaScript](./main.md) > [Call Stack, WebAPI, Event Loop & Call back Queue](./CallStack.md)_

# **JavaScript**

## **Call Stack, WebAPI, Callback Queue & Event Loop**

JavaScript is a single-threaded, non-blocking, asynchronous and concurrent language.

Since JavaScript is a single-threaded language if the code has any task which might take some time to complete or to perform an API request to get some data, so any such tasks/requests within our script will block the browser webpage from doing anything else like buttons disabled, page frozen, etc.,

Since this kind of behavior is not good, javascript handles this kind of asynchronous tasks in a different way to provide concurrency using WebAPI, Callback Queue( Microtask & Macro task ), and Event Loop.

<img src="./browserengine.png" alt="Browser Engine" style="width:70%;padding:0 15%;"/>

### **Call Stack:**

The synchronous code gets pushed directly to the call stack and is executed right away.

<img src="./callstack.png" alt="call stack" style="width:50%;padding:0 25%;"/>

### **WebAPI:**

The asynchronous code gets pushed to the call stack and since it cannot wait in call stack by blocking the webpage until it is complete, so it is pushed to WebAPI of the browser.

Few things like set timeouts, ajax calls, DOM are not part of the JavaScript language itself but are provided by the browser as part of WebAPI.

Below is an example that shows an how setTimeout works:

<img src="./webapi1.png" alt="setTimeout Example" style="width:60%;padding:0 20%;"/>

Below is an example that shows an how ajax requests and browser events works:

<img src="./webapi2.png" alt="ajax and events" style="width:60%;padding:0 20%;"/>


### **Callback Queue:**

The callback queue as per the V8 engine consists of a Microtask queue and a Macro task queue.

<img src="./callback.png" alt="callback queue" style="width:60%;padding:0 20%;"/>

### **Event Loop**:

