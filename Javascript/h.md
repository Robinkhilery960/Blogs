# JavaScript Runtime Environments: A Guide for Beginners

## How to Understand and Use the JS Engine, Web APIs, and Event Loop in Your Code 🚀

### [Click here to read at Hashnode ](https://robinkhilery.hashnode.dev/javascript-runtime-environments-a-guide-for-beginners)

Ever wondered how your JavaScript code comes to life? 🤔 How does JavaScript, the language we all know and love, handle your instructions and bring your web applications to life? 🚀 If you’ve found yourself pondering these questions, then you’re in the right place! 🙌

In this blog post, we’re going on an adventure into the heart of JavaScript - the runtime environment. This is where the magic happens, where your code goes from a series of instructions to dynamic, interactive web content. ✨

We’ll be exploring some intriguing concepts like the event loop, call stack, and callback queue. Ever heard of these? If not, don’t worry! 😊 We’ll be unravelling these mysteries together. 🔎

So are you ready to dive deep into the core of JavaScript’s runtime environment? Let’s embark on this exciting journey together! 🌊

## What is the JS runtime environment? 🌐

The JavaScript runtime environment provides access to built-in libraries and objects that are available to a program so that it can interact with the outside world and make the code work. 🛠️

It is a place where your JavaScript code is executed. It includes a JavaScript engine that interprets your code, a call stack that keeps track of your functions, and a heap that manages memory allocation. 💻 Additionally, it handles asynchronous tasks with mechanisms like the event loop and callback queue. 🔄

In the context of a browser, this is comprised of the following elements: 🌐

***The JavaScript engine*** 🔥

***Web APIs*** 🌐

***The task queues*** 📋

***The event loop*** 🔁

Let’s explore them all one by one. 👇

### The JavaScript engine 🚂

JS engine is a computer program whose work is to interpret the code written in the JavaScript programming language and execute those instructions on a computer system. 🖥️ This engine helps to convert our JavaScript program into a language that the computer can understand. 🧠

This means that to start writing JavaScript we don’t need to install any specific software because each web browser has its version of the JS engine that parses the code for us, Google Chrome and Chromium web browsers use V8, Firefox uses Spider Monkey etc. 🌎

In this article, we are going to focus on the V8 engine of Chrome. 🔍

### Heap: 🗑️

The heap in JavaScript is a region of memory where all objects, strings, and closures are stored. It’s like a large, mostly unstructured region of memory. 🧱

### The call stack 📚

The JS call stack is a data structure that helps the JavaScript engine keep track of the functions that are executed in a script. It works like a stack of plates, where you can only add or remove plates from the top. 🍽️ Similarly, you can only add or remove functions from the top of the call stack. This is called pushing and popping. 🔄

As the JS engine steps into a function, it is pushed onto the stack. When a function returns a value or gets sent to the Web APIs, it is popped off the stack. If a function doesn’t explicitly return a value then the engine will return undefined and also pop the function off the stack. This is what is meant by the term “JavaScript runs synchronously”; it is single-threaded, so can only do one thing at a time. ⏳

### Web APIs 🕸️

Web APIs are not part of the JavaScript language nor part of the JS engine itself, rather they are built on top of the core JavaScript language and provided by the browser giving you extra superpowers to use in your JavaScript code. 💪

One of the most common Web APIs used is [the DOM API], which allows developers to manipulate HTML and CSS, letting us create, change and even remove HTML and dynamically apply styles to our web pages. 🎨

In the background, the browser is using some complex lower-level code (e.g. C++ or Rust) to do the actual DOM manipulation. This complexity is abstracted away from you by the API providing some easier syntax to use in its place. 🙌

Features like event listeners, timing functions and AJAX requests all sit in the Web APIs container until an action gets triggered. A request finishes receiving its data, a timer reaches its set time or a click happens and this triggers a callback function to be sent to the callback queue. ⏰

### The task queues: Callback and Microtask Queue 📝

The task queues are data structures that store the tasks that are waiting to be executed asynchronously. There are two types of task queues: the callback queue and the microtask queue. 🚦

A microtask queue is a special kind of queue that stores small and urgent tasks that need to be executed as soon as possible, but after the current task is finished. A microtask is usually a callback function that is returned from a promise. A promise is an object that represents the completion or failure of an asynchronous operation, such as fetching data from a server. 📡

The callback queue is a place where the callback functions that are returned from the Web APIs are stored until they are ready to be executed. A callback function is a function that is passed as an argument to another function and is invoked after some event or condition is met. For example, when you use setTimeout() to delay the execution of a function, you are passing a callback function to the Web API. ⏳

The microtask queue and the callback queue are both managed by the event loop 🔁

### Event loop: 🔁

It is responsible for checking the call stack and the task queues, and executing the pending tasks when the call stack is empty. 🧐

The event loop monitors the call stack and the task queues, and follows these steps: 🚶‍♂️

If the call stack is empty, it will check the microtask queue first. If any microtasks are waiting in the queue, it will take the first one and push it to the call stack for execution. It will repeat this step until the microtask queue is empty.

If the microtask queue is empty, it will check the callback queue next. If there are any callbacks waiting in the queue, it will take the first one and push it to the call stack for execution. It will only do this once per iteration of the event loop.

If both queues are empty, it will wait for a new task to arrive from either queue. ⏲️

This way, the event loop ensures that asynchronous tasks are executed in a non-blocking manner, and that microtasks have higher priority than callbacks. 👍