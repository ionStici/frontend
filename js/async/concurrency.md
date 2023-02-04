[&larr; Back](./README.md)

# Concurrency Model and the Event Loop in JavaScript

## Table of Content

- [Why do we need an Event Loop?](#why-do-we-need-an-event-loop)
- [Concurrency in JavaScript](#concurrency-in-javascript)
- [What is the Event Loop?](#what-is-the-event-loop)
- [The Components of the Event Loop](#the-components-of-the-event-loop)
  - [The Heap](#the-heap)
  - [The Call Stack](#the-call-stack)
  - [The Event Queue](#the-event-queue)
  - [The Event Loop](#the-event-loop)

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

At a high level, the **event loop** is a system for managing code execution.

Data structures that are part of the JS engine: the _heap_ and the _call stack_. The heap and the call stack interact with Node and Web APIs, which pass messages back to the stack via an event queue. The event queue's interaction with the call stack is managed by an event loop.

All together, those parts maintain the order of code execution when we run asynchronous functions.

<br>

## The Components of the Event Loop

<br>

### The Heap

The _heap_ is a block of memory where our objects are stored in an unordered manner.

JavaScript variables and objects that are currently in use are stored in the heap.

<br>

### The Call Stack

The stack tracks what function is currently being run in the code.

When you invoke a function, a _frame_ for that function is added to the stack.

Frames connect the function's arguments and local variables from the heap.

Frames enter the stack in a _"last in, first out"_ order. Code example:

```js
function foo() {
  return function bar() {
    return function baz() {
      return "I love CodeCademy";
    };
  };
}
console.log(foo()()());
```

**The Call Stack** for the code example:

```
baz()
bar()
foo()
console.log(function)
global()
```

The currently executing function will be at the top of the stack.

In the code example, since we have nested functions, they will be added to the stack until until the innermost function has been executed.

When the function finishes executing, its frame is removed from the stack.

With `global()` we mean:

At the bottom of the call stack is added the **global execution context** which contains the global variables and lexical environment. Each subsequent frame for a called function has a function execution context that includes the function’s lexical and variable environment.

Again, the call stack tracks what function is currently being run in our code (the current execution context). When a function runs to completion, it is popped off of the call stack.

<br>

### The Event Queue

The **event queue** is a list of messages corresponding to functions that are waiting to be processed.

These messages are entering the event queue from sources such as various web APIs or async functions that were called and are returning additional events to be handled by the stack.

Messages enter the queue in a _first in, first out_ order.

No code is executed in the event queue, instead: it holds functions that are waiting to be added back into the stack.

<br>

### The Event Loop

Messages that are waiting in the event queue to be added back into the stack are added back via the event loop.

When the call stack is empty, if there is anything in the event queue, the event loop will add those to the stack for execution, one at a time.

1. First the event loop will check the stack to see if it is empty.
2. It will add the first waiting message.
3. It will repeat steps 1 and 2 until the stack has cleared.

Thanks to the event loop, JavaScript is a single-threaded, event-driven language that can run non-blocking code asynchronously.

<br>
