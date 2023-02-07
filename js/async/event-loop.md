[&larr; Back](./README.md)

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

_Answer:_ **All the asynchronous tasks will run in the web API environment of the browser.**

While synchronous code runs in the Call Stack.

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
