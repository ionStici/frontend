[&larr; Back](./modules.md)

# Modules Theory

## Table of Content

- [What are Modules?](#what-are-modules)
- [JavaScript Modules: Node.js and ES6](#javascript-modules-nodejs-and-es6)
- [A brief history of JavaScript Modules in the Browser](#a-brief-history-of-javascript-modules-in-the-browser)
- [Modules in Software Design in general](#modules-in-software-design-in-general)
- [Modules specifically in JavaScript](#modules-specifically-in-javascript)
- [How modules import other modules behind the scenes](#how-modules-import-other-modules-behind-the-scenes)

<br>

## What are Modules?

**Modules** are reusable pieces of code in a file that can be exported and then imported for use in another file. A modular program is one whose components can be separated, used individually, and recombined to create a complex system.

Instead of having the entire programm written within just one file, its components are broken up into separate module that each handle a particular task. This strategy is soemtiems called _separation of concerns_.

<details>
<summary>Advantages</summary>

By isolating code into separate files, called modules, we can:

<div></div>

- Find, fix, and debug code more easily.

<div></div>

- Reuse and recycle defined logic in different parts of your application.

<div></div>

- Keep information private and protected from other modules.

<div></div>

- Prevent pollution of the global namespace and potential naming collisions.

</details>

<br>

## JavaScript Modules: Node.js and ES6

Different ways of implementing modules depending on the runtime environment:

1. The Node runtime environment: `module.exports` and `require()` syntax.
2. The browser's runtime environment: ES6 `import` / `export` syntax.

<br>

## A brief history of JavaScript Modules in the Browser

The growth of web applications and of JavaScript as a popular programming language, led to the need for modularity.

Though libraries for implementing modules have existed for some time, syntax for natively implementing modules was only introduced in 2015 with the release of ECMAScript 6 (ES6). Since then, it has been adopted by most modern browsers and is the de facto approach for implementing modular applications in the browser.

### CommonJS Modules

Besides native ES6 modules and the module pattern, there are other module systems that have been used by JavaScript in the past, but which are not native JS. They rely on some external implementations. Two examples are: _AMD Modules and CommonJS Modules_.

**CommonJS** modules have been used in node.js for almost all of its existence. Only very recently ES6 modules have been implemented in node.js. The consequence of this is that almost all the modules in the _npm_ repository that we can use in our code still uses CommonJS module system. The reason for this is that npm was originally only intended for node, which as we said uses CommonJS. Only later, npm became the standard repository for the whole JavaScript world. Therefore, we will probably see a lot of CommonJS still around.

CommonJS syntax:

`export` + dot `.` + the name of the export

```js
export.sayHello = function() {}
```

Importing syntax:

```js
const { sayHello } = require(./file.js);
```

This is not working in the browser, but it would work in the node.js environment.

There are different module systems, and CommonJS is particularly important in the world of JavaScript.

In the long run, ES6 modules will hopefully and probably replace all of these different module systems.

<br>

## Modules in Software Design in general

A **Module** is a reusable piece of code that **encapsulates** implementation details of a certain part of our project. Usually, a module is a stanalone (separate) file.

**Exports** - we can export values (like functions) out of a module. Whatever we export from a module is called the public API.

**Imports** - we can import values from other modules. Importing modules are called dependencies.

Modules are a pattern that developers have been using in all languages for decades. Of course we can write code without modules, but for simple applications only. When the code base grows bigger and bigger, here start to be many advantages of using modules.

**Advantages of using modules:**

1. **Compose Software:** Modules are small building blocks that we put together to build complex applications;
2. **Isolate Components:** Modules can be developed in isolation without thinking about the entire code base;
3. **Abstract Code:** Implement low-level code in modules and import these abstractions into other modules;
4. **Organized Code:** Modules lead to a more organized code base;
5. **Reuse Code:** Modules allow us to easily reuse the same code, even across multiple projects;

<br>

## Modules specifically in JavaScript

Beginning with ES6, JavaScript has a native built-in module system. We did have modules before ES6, but we had to implement them ourselves or use external libraries. In ES6 modules, each file is a module.

_Differences between ES6 modules and JavaScript scripts:_

|                      | ES6 Module       | Scripts     |
| -------------------- | ---------------- | ----------- |
| Top-level variables: | Scoped to module | Global      |
| Default mode:        | Strict mode      | Sloppy mode |
| Top-level `this`:    | `undefined`      | `window`    |
| Imports and exports: | Yes              | No          |
| HTML linking:        | `type="module"`  | script      |
| File downloading:    | Asynchronous     | Synchronous |

<div></div>

1. In modules, all top-level variables are scoped (private) to the module by default.

   The only way an outside module can access a value that is inside of another module is by exporting that value. If we don't export, then no one from outside can see the variable.

   In scripts, all top-level variables are global. This can lead to problem like global namespace pollution, where multiple scripts try to declare variables with the same name and then these variables collide. Private variables are the solution to this problem.

2. ES6 modules are always executed in strict mode.

   Scripts are executed in sloppy mode by default.

3. At the top-level, the `this` keyword is always `undefined`.

   In scripts the `this` keyword points to the `window` object.

4. In modules, we can export and import values between modules using ES6 `import` and `export` syntaxes.

   _Node:_ importing and exporting can happen only at the top level, outside of any function or any `if` block.

   _Note:_ All imports are hoisted. It doesn't matter where in the code you are importing values, it's like the import statement will be moved to the top of the file. In practice, importing values is always the first thing that happens in a module.

5. In order to link a module to a HTML file, we need to use the script tag with the `type` attribute set to `module`.

6. File downloading for modules happens in an asynchronoys way.

   This is true for modules loaded by HTML, as well as for modules loaded by importing one module into another using the `import` syntax.

   Regular scripts are downloaded by default in a blocking synchronous way, unless we use the `async` or `defer` attributes on the script tag.

<br>

## How modules import other modules behind the scenes

Example: the main module named `index.js` is importing a value from other module.

When a peace of code is executed, first the code is parsed (the code is read without executing it). In this step imports are hoisted.

The whole process of importing modules happens before the code in the main module is executed.

The main importing module `index.js` imports other modules in a synchronous way, this means that only after all imported modules have been downloaded and executed, the main module `index.js` will finally be executed as well.

This is possible thanks to top-level imports, which make imports known before execution.

Thanks to top-level imports (outside of any code block), imports are known before execution, the engine can know all the imports and exports during the parsing phase, so while the code is being read before being executed.

If we could import a module inside of a function, then that function would have to be executed before the import, which couldn't be done without for the main module being executed first. In this case, modules could not be implemented in a synchronous way.

Why do we want modules to be loaded in a synchronous way? This is the easiest way in which we can do bundling and dead code elimination.

So, by knowing all dependencies between modules before execution, bundlers like webpack and parcel, can then join multiple modules together and eliminate dead code.

After the parsing phase and figuring out which modules need to import, then these modules are downloaded from the server. Downloading happens in a asynchronous way. Only the importing operation itself happens synchronously.

Then, after a module arrives, it is also parsed, and the modules exports are linked to the imports in the main module.

This connection between `import` and `export` syntaxes is a live connection. Export values are not copied to imports, instead the import is just a reference to the exported value. When the values changes in the exporting module, then the same value also changes in the importing module. This is unique to ES6 modules, other module systems do not work like this.

Next, after the execution of the imported modules,the importing main module is executed as well.

<br>
