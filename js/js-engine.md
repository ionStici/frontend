# JavaScript Engine

**JavaScript Engine** is a computer program that executes JavaScript code.

All browsers have their own JS engine. The most well known engine is Google's V-8, which powers Google Chrome and Node.

JavaScript engine components:

- **The Call Stack** is where the code is executed using _execution contexts_.
- **The Heap** is an unstructured memory pool which stores all the objects.

<br>

## Table of Content

- [How JavaScript Code is Compiled to Machine Code?]()
- [The Modern Just-In-Time Compilation of JavaScript]()
- [Browsers and Node.js as the JavaScript Runtime]()

<br>

## How JavaScript Code is Compiled to Machine Code?

For computers to understand code, the source code first have to be converted to machine code.

**Compilation:**

- The program source code is converted to machine code.
- Any application on our computer has been compiled before.

**Interpretation:**

- An _Interpreter_ runs through the source code and executes it line by line.
- The code is executed and converted to machine code all at the same time.

**Just-In-Time Compilation:**

- JavaScript used to be purely interpreted language. But nowadays, to increase its performance, modern JavaScript engine use a mix between compilation and interpretation.
- The entire source code is converted to machine code, and then executed immediately.

<br>

## The Modern Just-In-Time Compilation of JavaScript

1. First step: As the code enters the JavaScript engine, the code is parsed into a data structure called the _Abstract Syntax Tree (AST)_. This step is also when the code is checked for syntax errors. The resulting tree will be later used to generate the machine code.

2. Second step: Compilation. It takes the generated AST and compiles it into machine code.

3. Third step: Execution. The compiled machine code is executed right away in the JavaScript engine call-stack.

**JavaScript optimization strategies:** an unoptimized version of machine code is created in the beginning, so that it can start execution as fast as possible. Then in the background, this code is being optimized and recompiled during the already running program execution. And this can be done multiple times, and after each optimization, the unoptimized code is simply swept for new more optimized code, without ever stopping the execution of course. And this process is what makes modern engines such as V-8 so fast. And all this parsing, compilation and optimization happens in some special threads inside the engine that we cannot access from our code. So completely separate from the main thread that is running into call-stack executing our own code. Different engines, implement this in slightly different ways, but in a nutshell, this is what modern just-in-time compilation looks like for JavaScript.

<br>

## Browsers and Node.js as the JavaScript Runtime

A JavaScript runtime environment is where the JavaScript code is executed.

It also contains all the JS related stuff. The heart of the JS runtime is the JS engine.

In the **browser runtime**, we get access to web APIs (DOM, Timers, etc.). Web APIs are provided to the engine, but are not part of the JS language itself, it simply gets access to these APIs through the global window object.

Next, a JS runtime also includes a **callback queue**, which is a data structure that contains all the callback functions that are ready to be executed. For example, a **callback function** ready to run, is placed first into the callback queue, and only when the call stack is empty the callback function is passed to the stack to be executed. This is doen through the **event loop**, which takes the callback functions from the callback queue and puts them in the call stack so that they can be executed.

### Node.js Runtime Environment

With **Node.js runtime** we can run JavaScript code outside of browsers. Here we don't have web APIs, but instead we have multiple C++ bindings, thread pool, and more.
