[&larr; Back](./README.md)

# Concurrency Model and the Event Loop in JavaScript

## Table of Content

- [Why do we need an Event Loop?](#why-do-we-need-an-event-loop)
- [Concurrency in JavaScript](#concurrency-in-javascript)
- [What is the Event Loop?](#what-is-the-event-loop)
- [The Components of the Event Loop](#the-components-of-the-event-loop)
- [**In-depth Asynchronous JavaScript**](#asynchronous-behind-the-scenes-the-event-loop)

<br>

## Why do we need an Event Loop?

JavaScript is a **single-threaded** language. This means that two statements can't be executed simultaneously.

For example, a heavy loaded `for` loop will stop the code execution for some seconds, blocking the next line of code.

But, we can run _non-blocking_ code in JavaScript using the **Event Loop**.

For example, the `setTimeout` function runs asynchronously thanks to the Event Loop.

Even so JavaScript is still single-threaded, the event loop is enabling something called **concurrency**.

<br>

## Concurrency in JavaScript

**Concurrency** in programming means that two or more procedures are executed on the same shared resources (e.g. threads, processes, CPU cores).

Since JS is single-threaded, it isn't using the traditional way of concurrency.

However, we can emulate concurrency using the event loop.

At a hign level, asynchronous code can be pushed to web APIs and then directed back into the stack via the event queue and event loop.

<br>

## What is the Event Loop?

The **event loop** is a system for managing code execution.

The heap and the call stack interact with Node and Web APIs, which pass messages back to the stack via an event queue. The event queue's interaction with the call stack is managed by an event loop.

All together, those parts maintain the order of code execution when we run asynchronous functions.

<br>

## The Components of the Event Loop

- **The Heap** is a block of memory where our objects are stored in an unordered manner. JavaScript variables and objects that are currently in use are stored in the heap.

<br>

- **The Call Stack** tracks what function is currently being run in the code.

  When we invoke a function, a _frame_ for that function is added on the stack. Frames connect the function's arguments and local variables from the heap. Frames enter the stack in a _"last in, first out"_ order.

  ```js
  function foo() {
    return function bar() {
      return function baz() {
        return "I love CodeCademy";
      };
    };
  }
  console.log(foo()()());

  // The Call Stack:
  // 5. baz()
  // 4. bar()
  // 3. foo()
  // 2. console.log(function)
  // 1. global()
  ```

  The currently executing function will be at the top of the stack. Nested frames are added on top of its parent frame. When the function finishes executing, its frame is removed from the stack.

  At the bottom of the Stack we have the **global execution context** `global()` which contains the global variables and lexical environment. Each subsequent frame for a called function has a function execution context that includes the function’s lexical and variable environment.

  _Review:_ The Call Stack tracks what function is currently being run in the code (the current execution context). When a function runs to completion, it is popped off of the call stack.

<br>

- **The Event Queue** is a list of message corresponding to functions that are waiting to be processed.

  These messages are entering the event queue from sources such as web APIs or async functions that were called and are returning additional events to be handled by the stack.

  Messages enter the queue in a _first in, first out_ order.

  No code is executed in the event queue, instead it holds functions that are waiting to be added back into the stack.

<br>

- **The Event Loop** coordinates the waiting messages in the event queue and their related callbacks.

  When the call stack is empty and if there is anything in the event queue, the event loop will add those to the stack for execution, _one at a time_.

  1. The event loop ensures that the stack is empty.
  2. If it is, it will add the first waiting message.
  3. It will repeat steps 1 and 2 until the stack and queue has cleared.

  Thank to the event loop, JavaScript is a single-threaded, event-driven language that can run non-blocking code asynchronously

<br>
<br>

<hr>

<br>
<br>

# Asynchronous Behind the Scenes: The Event Loop

JavaScript is a **single-threaded** language. This means that two statements can't be executed simultaneously.

## Table of Content

- [JavaScript Engine Components](#javascript-engine-components)
- [Concurrency model](#concurrency-model)
- [Callback Queue](#callback-queue)
- [Event Loop](#event-loop)
- [Microtasks queue](#microtasks-queue)
- [The Event Loop in Practice](#the-event-loop-in-practice)

<br>

## JavaScript Engine Components

- **Call Stack** is where code is executed through execution contexts.
- **The Heap** is a block of memory where objects are stored.
- **Web APIs Environment:** here we have APIs provided to the engine, but which are not part of the JavaScript language.
- **Callback queue:** a data structure that holds all the ready to execute callbacks that are attached to some event that has occurred.

Whenever the call stack is empty, the **Event Loop** takes callbacks from the _callback queue_ and puts them into the stack to be executed.

The **Event Loop** is the essential piece that makes _asynchronous behavior_ possible and it's the reason why we can have a _non-blocking concurrency model_ in JavaScript.

A **Concurrency Model** refers to the system a programming language uses to handle non-blocking behavior.

<br>

## Concurrency model

How does the JavaScript concurrency model works in an asynchronous way if JavaScript engine is build around the idea of a single thread?

_Answer:_ **All the asynchronous tasks will run in the web API environment of the browser.** While synchronous code runs in the Call Stack.

_Example:_ The callback of the `setInterval` function will be registered in the web APIs environment and will be placed and executed in the call stack only when the timer finishes.

_Example:_ Ajax call using the fetch API. The asynchronous fetch operation will happen in the web APIs environment. We use the `then()` method to handle the promise, which in turn will register a callback in the web APIs environment.

<br>

## Callback Queue

Registered asynchronous callbacks will kept waiting in the web APIs environment until a certain event happened and then it is placed in line in the _callback queue._

The **Callback Queue** is an ordered list of all the callback functions that are in line to be executed.

A callback of an asynchronous task will be put into the callback queue to wait for its execution.

If in the callback queue were other callbacks waiting in line, then the new callbacks would go straight to the end of the queue, and wait for their turn to run. This has big implications.

_Example:_ A `setTimeout` with 5 seconds timer - after the timer finishes, its callback will be put on the callback queue. In case there already were other callbacks waiting, and for example it took 1 second to run these callbacks, then our timer's callback would run after 6 seconds instead of the 5 seconds that we actually specified. The timer's duration that we define is not a guarantee, the only guarantee is that the callback will not run before 5 seconds. So it depents on the state of the callback queue.

The callback queue also handles callbacks coming from the DOM events likes clicks. DOM events are not asynchronous behavior, but still they use the callback queue to run their attached callbacks. A DOM event is handled by the callback queue just as we described with the asynchronous `setTimeout` function.

<br>

## Event Loop

The **Event Loop** first will look into the call stack and determine whether or not it's empty (expect for the global context). If the call stack is indeed empty, which means that there is currently no code being executed, then it will take the first callback from the _callback queue_ and put it on the stack to be executed. This process is called **an event loop tick**.

The **Event Loop** has the important job of doing coordination between the call stack and callbacks from the callback queue.

Asynchronous tasks does not happen in the JS engine, it's the runtime who manages all the asynchronous behavior, and it's the event loop who decides which code will be executed next. The engine itself executes whatever code you gave it.

_The web APIs environment (1)_, _the callback queue (2)_, _the event loop (3)_, all together make possible the execution of asynchronous code, even with only one thread of execution in the engine.

<br>

## Microtasks queue

With promises thinks work in a different way.

The `fetch` function getting data from an Ajax call using a promise.

Promise callbacks from `then()` methods are handled by the **microtasks queue** instead of the callback queue.

What is special about the _microtasks queue_ is that it has priority over the _callback queue_. The event loop will check if there are any callbacks in the microtasks queue, and if there are then it will run all of them before running any callbacks from the regular callback queue. We call promise callbacks: **microtasks**.

If one microtask adds a new microtask, then that new microtask is also executed before any callbacks from the callback queue.

The idea of running asynchronous code with regular callbacks and with microtasks coming from promises is very similar. The only different is that callbacks go into different queues, and that the event loop gives microtasks priority over regular callbacks.

_Consider:_ We can promisify regular callbacks into promise based callbacks.

<br>

## The Event Loop in Practice

```js
console.log("Test Start");

setTimeout(() => console.log("0 seconds timer"), 0);

Promise.resolve("Resolved Promise 1").then((data) => console.log(data));

Promise.resolve("Resolved Promise 2").then((data) => {
  for (let i = 0; i < 1000000000; i++) {}
  console.log(data);
});

console.log("Test End");

// OUTPUT
// Test Start
// Test End
// Resolved Promise 1
// Resolved Promise 2
// 0 seconds timer
```

- After 0 seconds the callback from `setTimeout` will be put in the callback queue.

- First, top-level code runs. In our code example we have two top-level `console.log` methods.

- The timer and promises both finish at the exact same time.

- The timer appears first in the code, finishes first, its callback will be put on the callback queue first, but it will not be executed first, because of the microtasks queue.

- The callbacks of the resolved pormises will be put on the microtasks queue, and this microtasks queue has priority over the callback queue.

- The callbacks from the microtasks queue are executed first.

- The implication of the fact that microtasks have priority over regular callbacks is that if one of the microtasks takes a long time to run, then the timer will be delayed and not run after exactly 0 seconds as we specified, it will wait for the microtasks to run first.

- From our code example, the second promise runs a heavy task which will take some time. The timer callback from the callback queue will be deplayed because of this.

<br>
