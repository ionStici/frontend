[&larr; Back](./README.md)

# The Call Stack

## Table of Content

- [Call Stack](#call-stack)
- [Execution Contexts](#execution-contexts)
- [What is inside an execution context?](#what-is-inside-an-execution-context)

<br>

## Call Stack

**The Call Stack** - a place where execution contexts get stacked on top of each other in order to keep track of where we are in the program execution. The execution context that is on top of the stack, is the one that is currently running. When it finished running, it will be removed from the stack and the execution will go back to the previous context.

When we close the browser tag, the program is really finished, the global execution context is popped off the stack.

<br>

## Execution Contexts

The code finished compiling, now ready to be executed. How JavaScript code is executed?

1. A **Global execution context** is created for the _top-level code_.

   - Top-level code (like variables) is code that is not inside any code block, like functions or `if` statements.
   - Functions will also be declared as top-level code, but the code inside the function body is considered to be block scoped.

<div></div>

2. Once the top-level code finished, functions start to execute as well.

   - For every function & method call, a new **execution context** will be created.
   - All the execution contexts together make up the **call stack**.

<div></div>

3. When all functions are done executing, the engine will keep waiting for callback functions to arrive (events).

<div></div>

An **execution context** is like an environment in which JavaScript code is executed. This environment stores information like local variables, or arguments passed into a function.

- JavaScript code always runs inside an execution context.
- In any JavaScript project, there is only one **global execution context** (as the default context), where top-level code is executed.

<br>

## What is inside an execution context?

The content of an execution context: Variable environment + Scope Chain + `this` keyword.

These are generated in the creation phase which happens right before execution.

1. **Variable environment**

   - In this environment all variables and function declarations are stored.
   - Also, there is a special `arguments` object (array), containing all the arguments that were passed into the function that the current execution context belongs to.

<div></div>

2. **Scope Chain**

   - The scope chain is a way to provide systematic access to variables and functions that the current execution context has access to.

<div></div>

3. **The `this` keyword**

   - Consider: Execution contexts belonging to arrow functions do not get their own `arguments` object or the `this` keyword. Instead, they will use the `arguments` object and the `this` keyword from their closest regular function parent.

<div></div>

<br>
