# Deep Dive In Javascript!

<!-- HEADER -->
<div align="center">
  <a href="https://github.com/Saeid-Barzegar/deep-dive-in-javascript">
    <img style="border-radius: 15px;" src="images/JavaScript_logo.svg" alt="Logo" width="100" height="100">
  </a>

  <h3 align="center">JavaScript Concepts in Depth!</h3>

  <p align="center">
    A Comprehensive Exploration of Fundamental JavaScript Concepts
    <br />
    <a href="https://github.com/Saeid-Barzegar/deep-dive-in-javascript/blob/main/README.md"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/Saeid-Barzegar/deep-dive-in-javascript/blob/main/README.md">Read More</a>
    ·
    <a href="https://github.com/Saeid-Barzegar/deep-dive-in-javascript/issues">Comments</a>
  </p>
</div>

 <br style="margin-bottom: 200px"/>

<!-- TABLE OF CONTENTS -->
## Table Of Contents
<ol style="margin-top: 10px">
  <li><a href="#read-bofore-start">Read Bofore Start</a></li>
  <li><a href="#chapter-1">Chapter 1: Engine and Runtime</a></li>
  <li><a href="#license">License</a></li>
  <li><a href="#contact">Contact</a></li>
</ol>


## Read Bofore Start
This collection is all about the important aspects of JavaScript, with the main focus being on key concepts to understand what exactly JavaScript is and how it works in depth. The basics of syntax learning will be skipped while ensuring it doesn't compromise the core understanding 
<br /><br /> Then it's important to know before start:
* It's not a zero to mastery course!
* Prior familiarity with JavaScript basics is recommended before diving in.
* This repository will be open for collaboration, inviting everyone to contribute and enhance its comprehensiveness and usability for a global audience.



# Chapter 1:

### Engine and Runtime

### Javascript Runtime:

A JavaScript runtime is an environment in which JavaScript code is executed. It provides the necessary infrastructure and resources for running JavaScript programs, such as a web browsers or server-side environments like Node.js.

For example, both the Chrome web browser and Node.js are JavaScript runtimes that utilize the V8 engine as their JavaScript execution environment.

We can say, the JavaScript runtime is a program that extends the JavaSciript engine and provides additional functionalities, so it can interact with the outside world. Also, the JS runtime provides features/APIs to build Javascript based software. This means both browsers, and JavaScript based frameworks have runtimes, but different ones based on their needs.

<i>The list below includes the key concepts of JavaScript runtimes. We'll provide a brief overview for each and go through them one by one as we proceed.</i>

1. <a href="#1-javascript-engine"><b>JavaScript Engine</b></a>
2. <a href="#2-event-loop"><b>Event Loop</b></a> 
3. <a href="#3-promises-and-asyncawait"><b>Promises and Async/Await</b></a> 
4. <a href="#4-memory-management"><b>Memory Management</b></a> 
5. <a href="#5-global-object"><b>Global Object</b></a> 
6. <a href=""><b>Environment-specific APIs</b></a> 
7. <a href=""><b>Modules and Scoping</b></a> 
8. <a href=""><b>Concurrency Model</b></a> 
9. <a href=""><b>Error Handling</b></a> 
10. <a href=""><b>Event Emitters and Event Handling</b></a> 


<hr />

### 1. JavaScript Engine:
<p><a href="#javascript-runtime">Back</a></p>
Basically, a JavaScript engine is a computer program that interprets and executes JavaScript codes and it performs several important tasks, including:

<ul>
  <li>
    <strong>Parsing:</strong>
    <span>The engine takes the JavaScript code as input and breaks it down into smaller pieces that can be understood by the computer. This process involves converting the human-readable code into a format that the engine's internals can work with.</span>
  </li>
  <li>
    <strong>Compilation:</strong>
    <span>In some modern JavaScript engines, the parsed code is compiled into an intermediate form, like bytecode or machine code, for more efficient execution. This compilation step can help improve the performance of executing JavaScript code.</span>
  </li>
  <li>
    <strong>Optimization:</strong>
    <span>Some JavaScript engines employ various optimization techniques to enhance the speed and efficiency of code execution. These techniques can include inlining functions, reordering instructions, and identifying performance bottlenecks.</span>
  </li>
  <li>
    <strong>Execution:</strong>
    <span>Once the code is parsed and, if applicable, compiled and optimized, the engine begins executing the instructions. It interprets the code line by line, performing the operations specified by the JavaScript statements.</span>
  </li>
  <li>
    <strong>Memory Management:</strong>
    <span>JavaScript engines manage memory allocation and deallocation to store variables, objects, and data structures used during code execution. They also include garbage collection mechanisms to free up memory occupied by objects that are no longer needed</span>
  </li>
</ul>


### Popular JavaScript engines:
<ul>
  <li>
    <strong>V8:</strong>
    <span>Developed by Google, Mainly used in Chrome browser and the Node.js runtime.</span>
  </li>
  <li>
    <strong>SpiderMonkey:</strong>
    <span>Developed by Mozilla and used in the Firefox browser.</span>
  </li>
  <li>
    <strong>JavaScriptCore:</strong>
    <span>Developed by Apple and used in the Safari browser. It's also the foundation for the JavaScript runtime in iOS and macOS applications.</span>
  </li>
  <li>
    <strong>Chakra:</strong>
    <span> Developed by Microsoft, Chakra was the engine used in the Edge browser before it transitioned to using Chromium's Blink engine.</span>
    <p><a href="https://en.wikipedia.org/wiki/List_of_ECMAScript_engines">Full List of Javascript Engines</a></p>
  </li>
</ul>

<br />
<hr />

### 2. Event Loop
<p><a href="#javascript-runtime">Back</a></p>

The event loop is one of the fundamental concepts in JavaScript (and many other programming languages) that enables asynchronous programming and non-blocking behavior. It's especially important in environments like web browsers and Node.js, where applications often need to perform tasks concurrently without blocking the entire program's execution.

At a high level, the event loop is a mechanism that continually checks a queue of tasks (often referred to as the "task queue" or "callback queue") and executes them in a specific order. Here's how the event loop works:

<img src="images/Javascript-event-loop.png" />

1. <b>Call Stack:</b>
<span>The call stack is a data structure that keeps track of function calls in your program. When a function is called, a new frame is added to the top of the call stack, representing that function's execution context. As functions complete their execution, their frames are removed from the stack in a last-in, first-out (LIFO) order. The call stack is used to manage the flow of synchronous code execution.
Synchronous code runs in a single-threaded manner, which means that only one function is executed at a time. The call stack ensures that the program knows which function is currently being executed and how to return to the appropriate context once that function completes.</span>

2. <b>Callback Queue: </b>
<span> The callback queue (sometimes referred to as the task queue) is a queue that holds callback functions from completed asynchronous operations. When an asynchronous operation completes (such as a timer set by setTimeout or a network request), its associated callback is placed in the callback queue rather than being executed immediately. The callback queue operates on a first-in, first-out (FIFO) basis.
The event loop's job is to continually check whether the call stack is empty. If it is, the event loop dequeues callbacks from the callback queue and adds them to the call stack for execution. This process allows asynchronous tasks to be executed in a non-blocking manner.</span>

3. <b>Event Loop Iteration :</b>
<span>The event loop continually checks if the call stack is empty. If it is, the event loop takes the first callback function from the task queue and adds it to the call stack for execution. This process is known as "dequeuing" or "polling" the task queue.</span>

4. <b>Callback Execution:</b>
<span>The callback function on the top of the call stack is executed. If the callback involves asynchronous operations (such as making another asynchronous request or setting a timeout), those operations are initiated and their callbacks are placed in the task queue.</span>

5. <b>Repeat:</b>
<span>The event loop continues this process of checking the call stack, dequeuing tasks from the task queue, and executing callback functions. This loop keeps running as long as there are tasks in the queue and the call stack is empty.</span>


This mechanism ensures that asynchronous operations can be initiated without blocking the main execution thread. Instead of waiting for an operation to complete, the program can continue executing other tasks and respond to events.

It's important to note that the event loop operates in a single-threaded environment, which means that only one task is executed at a time. As a result, long-running synchronous operations can block the event loop and make the application less responsive. To mitigate this, JavaScript developers often use techniques like Promises, async/await, and splitting tasks into smaller chunks to ensure that the event loop remains available for handling other tasks.

<br />
<hr />

### 3. Promises and Async/Await
<p><a href="#javascript-runtime">Back</a></p>

Promises and Async/Await are both concepts in JavaScript that pertain to handling asynchronous operations in a more structured and manageable manner. While they are language features and programming paradigms, they play a significant role within the context of a JavaScript runtime.

#### Promises:
Promises are a way to manage asynchronous operations in JavaScript. They provide a clean and predictable way to handle the results (either success or failure) of asynchronous tasks. A Promise is an object that represents a value that may be available now, in the future, or never. It has three states: pending (initial state), fulfilled (resolved with a value), and rejected (resolved with an error).

Promises allow you to attach callback functions to be executed when the asynchronous task completes. This makes it easier to manage complex chains of asynchronous operations and handle errors more effectively. Promises help mitigate the "callback hell" that can arise when dealing with nested callbacks.

When you make use of APIs like <b>fetch</b> for network requests or timers like <b>setTimeout</b>, they return Promises. The Promise-based approach allows the runtime to manage these tasks without blocking the main thread.

#### Async/Await:
Async/Await is a more recent addition to JavaScript and builds upon the Promise concept. It provides a way to write asynchronous code that resembles synchronous code, making it more readable and easier to understand. Async functions return Promises implicitly, and within an async function, you can use the await keyword to pause the execution until a Promise resolves. This keeps the event loop free for other tasks while waiting for asynchronous operations to complete.

Both Promises and Async/Await are crucial concepts for modern JavaScript development and are integral to how the JavaScript runtime handles asynchronous tasks in a way that's more readable, maintainable, and efficient.

<br />
<hr />

### 4. Memory Management
<p><a href="#javascript-runtime">Back</a></p>


Memory management in a JavaScript runtime involves the allocation, usage, and deallocation of memory resources for variables, objects, data structures, and other resources used by your JavaScript code. Effective memory management is essential to ensure that your program uses memory efficiently, avoids memory leaks, and maintains good performance.

Here's how memory management works in a JavaScript runtime:

1. <b>Allocation:</b>
<span>When you create variables, objects, arrays, or any data structures in your code, the runtime allocates memory to store their values. This memory allocation happens dynamically as you run your code.</span>

2. <b>Garbage Collection:</b>
<span>Over time, as your code runs, objects and data structures that are no longer needed become "garbage." Garbage collection is the process of identifying and freeing up memory occupied by these unused objects. This prevents memory leaks, where memory is allocated but not properly released, leading to increased memory usage and potential performance issues.</span>

3. <b>Reference Counting:</b>
<span>One common garbage collection technique involves counting references to objects. If an object's reference count drops to zero, meaning it's no longer accessible, the runtime knows it can safely deallocate the memory occupied by that object.</span>

4. <b>Mark and Sweep:</b>
<span>Another garbage collection technique, often used in modern JavaScript runtimes, is the "mark and sweep" algorithm. It involves marking all objects that are reachable from the program's roots (global objects, function scopes, etc.). Any unmarked objects are no longer needed and can be safely deallocated.</span>

5. <b>Memory Leaks:</b>
<span>Despite the best efforts of the runtime's garbage collector, memory leaks can occur if references to objects are unintentionally kept longer than necessary. For instance, if an object still has references even though it's no longer needed, it won't be collected. Common causes of memory leaks include circular references or not properly unregistering event listeners.</span>

6. <b>Optimizations:</b>
<span> Some JavaScript runtimes use memory optimization techniques, such as object pooling, where frequently used objects are recycled instead of being created and destroyed repeatedly, reducing memory allocation overhead.</span>

Memory management in a JavaScript runtime is mostly automatic, thanks to the runtime's garbage collector. However, developers can still influence memory management by writing efficient code, being mindful of object references, and avoiding unnecessary memory consumption. It's important to be aware of memory usage, especially in long-running applications, to ensure that your program remains performant and doesn't suffer from memory-related issues.

<br />
<hr />

### 5. Global Object
<p><a href="#javascript-runtime">Back</a></p>

The Global Object, also known as the global scope, is a fundamental concept in JavaScript runtimes. It serves as the entry point for interacting with the runtime environment and provides access to various built-in objects, functions, and APIs. The specifics of the Global Object can vary between different runtime environments, such as browsers and Node.js.

Here are some key aspects of the Global Object:

1. <b>Access to Built-In Objects:</b>
<span>The Global Object provides access to several important built-in objects and functions. These include objects like <b>Object</b>, <b>Array</b>, <b>String</b>, and <b>functions</b> like <b>parseInt</b> and <b>setTimeout</b>. You can use these objects and functions directly without needing to qualify them with any namespace.</span>

2. <b>Browser Environment (Window Object):</b>
<span>In browser runtimes, the Global Object is often referred to as the "window" object. It represents the global scope for JavaScript code running in a web page. It not only provides access to core JavaScript functionality but also exposes browser-specific APIs like the Document Object Model (DOM) API, which allows you to manipulate web page elements.</span>

3. <b>Node.js Environment (Global Object):</b>
<span> In the Node.js runtime, the Global Object is known as the "global" object. It provides access to core JavaScript functionality and Node.js-specific modules and APIs. The global object in Node.js serves as the starting point for accessing the features provided by the Node.js runtime, such as the require function for importing modules and the process object for interacting with the Node.js process.</span>

4. <b>Custom Global Variables:</b>
<span>You can attach custom variables and functions to the Global Object. However, it's generally recommended to avoid cluttering the global scope with too many variables, as this can lead to naming conflicts and make code harder to maintain.</span>

5. <b>Scope and Execution Context:</b>
<span>Code executed in the global scope runs within the context of the Global Object. Variables declared in the global scope become properties of the Global Object.</span>

6. <b>Window vs. Worker Environments:</b>
<span>In browser runtimes, there's a distinction between the "window" object (main thread) and the "WorkerGlobalScope" object (web workers) for managing separate threads of execution.</span>

The Global Object provides a convenient way to access core language features and interact with the runtime environment. However, due to its global nature, it's important to exercise caution when using it to avoid unintentional variable conflicts and ensure code maintainability. It's often a good practice to encapsulate your code within modules or namespaces to limit the use of the global scope.

<p align="right"><a href="#table-of-contents">back to top</a></p>
