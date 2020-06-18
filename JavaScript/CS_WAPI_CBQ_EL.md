_[General](../README.md) > [JavaScript](./main.md) > [Call Stack, WebAPI, Event Loop & Call back Queue](./CS_WAPI_CBQ_EL.md)_

# **JavaScript**

## **Call Stack, WebAPI, Callback Queue & Event Loop**

`JavaScript is a High-level, single-threaded, garbage-collected, interpreted, or just in time compiled, prototype-based, multi-paradigm, dynamic language with a non-blocking event loop.`

Since JavaScript is a single-threaded language if the code has any task which might take some time to complete or to perform an API request to get some data, so any such tasks/requests within our script will block the browser webpage from doing anything else like buttons disabled, page frozen, etc.,

Since this kind of behavior beats the whole purpose as there as many multi-threaded languages out there, javascript handles this kind of asynchronous tasks in a different way to provide concurrency using WebAPI, Callback Queue( Microtask & Macro task ), and Event Loop.

<img src="./browserengine.png" alt="Browser Engine" style="width:50%;padding:0 25%;"/>

### **Call Stack:**

The synchronous code gets pushed directly to the call stack and gets executed right away.

The call stack is a data structure that is responsible for executing the code from top to bottom. And each block of code is pushed onto the call stack while parsing. All the synchronous parts get executed in a LIFO manner, but the asynchronous parts are moved to the WebAPI as they are usually of blocking behavior.

<img src="./callstack.png" alt="call stack" style="width:50%;padding:0 25%;"/>

### **WebAPI:**

The asynchronous code gets pushed to the call stack and since it cannot wait in call stack by blocking the webpage until it is complete, so it is pushed to WebAPI of the browser.

Few things like set timeouts, ajax calls, DOM are not part of the JavaScript language itself but are provided by the browser as part of WebAPI.

**Below is an example that shows how setTimeout works:**

The consoles get pushed onto call stack and get executed right away, but setTimeout gets pushed to the call stack and then sent to WebAPI where the timer starts running, and once the time completes, the callback function gets pushed onto callback queue. When the call stack doesn't have any pending tasks to execute, the event loop runs and moves the callback functions from the callback queue to the call stack.

<img src="./webapi1.png" alt="setTimeout Example" style="width:60%;padding:0 20%;"/>

**Below is an example that shows how AJAX requests and Browser events work:**

The console gets pushed onto the call stack and gets executed right away, but click event and, ajax call gets pushed to the call stack and then sent to the WebAPI where it waits till click event is performed and pushes the callback function to callback queue also the URL gets hit to send the request, and once the data is retrieved the callback function gets pushed onto callback queue. When the call stack doesn't have any pending tasks to execute, the event loop runs and moves the callback functions from the callback queue to the call stack.

<img src="./webapi2.png" alt="ajax and events" style="width:60%;padding:0 20%;"/>


### **Callback Queue:**

The callback queue as per the V8 engine is divide into a Microtask queue and a Macro task queue.

Things like promises, async function calls are considered as microtasks and get priority over things like setTimeouts, events, etc., which are macro tasks. And they are moved to either microtask queue or macrotask queue depending upon the type of task.

When the call stack is empty then the event loop picks tasks from the microtask queue till it is empty then it looks at the macrotask queue to push them onto the call stack.

<img src="./callback.png" alt="callback queue" style="width:60%;padding:0 20%;"/>

### **Event Loop**:

The Even loop as the name suggests, is a single-threaded continuous process that is responsible for executing the code that is present in the call stack. Later it looks for any events or queued tasks in the callback queue once everything in the call stack is executed. Then it moves all the events and tasks from the callback queue based on priority until everything from the queue is executed.

