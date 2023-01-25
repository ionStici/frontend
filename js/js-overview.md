[&larr; Back](./README.md)

# JavaScript Overview

## Table of Content

- [JavaScript Introduction](#javascript-introduction)
- [JavaScript Definition](#javascript-definition)
- [JavaScript Over Time](#javascript-over-time)

<br>

## JavaScript Introduction

**JavaScript** is the programming language of the web. With JavaScript we can:

- Build web apps in the browser, load data from remote servers.
- Add dynamic and interactive effects to any webpage, manipulate content or CSS styles.
- JavaScript can be used for animating, rendering and scaling.
- JavaScript offers a wide range of frameworks and libraries for building complex applications.

_JavaScript libraries_ - consists of functions that an application can call to perform a task.

_JavaScript frameworks_ - defines how a developer design an application.

All these frameworks and libraries are 100% based on JavaScript, so you have to become really good at JS before learning and using any of these tools.

<br>

### Server-side JavaScript

JavaScript can be used in both the frontend and backend of web development.

It can be integrated with other languages to communicate and interact with databases.

Using Node.js we can build Server-side JavaScript. With node we can execute JavaScript outside the browser, for example on a web server, this enables us to create backend scalable web apps, messaging platforms, multiplayer games,

<br>

### Beyond the web

With Electron.js framework we can develop desktop applications for different devices regardless of the operating system.

With modern tools like React Native, we can develop native mobile apps with JS, for any operating system.

In addition, JavaScript has the potential of expanding into other innovative technologies such as virtual reality and gaming.

<br>

## JavaScript Definition

JavaScript is a programming language with the following characteristics:

<br>

- **High-Level**

  Every program that runs on a computers needs some hardware resources to do its work, such as memory and the CPU.

  There are low-level languages, such as C, where you have to manually manage these resources, for example asking the computer for memory to create a new variable.

  With high-level languages, such as JavaScript and Python, we do not have to manage resources at all, because these languages have _abstractions_ that take all of that work away from us, so we don't have to think about complex stuff like managing the computer's memory while it runs our program.

  This makes the languages easier to learn and to use, but the downside is that the programs will never be as fast or as optimised as for example C programs.

<br>

- **Garbage-Collected**

  Takes memory management away from us developers. This refers to an algorithm inside the JavaScript engine, which automatically removes old and unused objects from the computer memory, in order not to clog it up with unnecessary stuff.

<br>

- **Interpreted or just-in-time compiled**

  The computer processor only understands zeros and ones.

  Ultimately, every single program needs to be written in zeros and ones, called: **machine code**. Since that is not really practical to write, we write human-readable code, which is an abstraction over machine code.

  This human-readable code, eventually needs to be translated to machine code, this step can be either **compiled** or **interpreted**.

  This step is necessary in every single programming language.

  In the case of JavaScript, this happens inside the JavaScript engine.

<br>

- **Multi-Paradigm**

  In programming, a paradigm is an approach and midnset of structuring code, which will direct your coding styles and techniques.

  JavaScript is a multi-paradigm language, which means that it is flexible and versatile, so we can use all kinds of different programming styles, such as _imperative_ and _declarative_ programming.

  Popular paradigms: Procedural programming, Object-oriented programming, functional programming.

  Many languages follow only one paradigm, but JavaScript can do all of them.

<br>

- **Prototype-based, Object-oriented**

  The object-oriented nature of JavaScript is a prototype-based object-oriented approach.

<br>

- **First-class functions**

  In a language with _first-class_ functions, functions are treated as variables. We can pass them into other functions and return them from functions.

  This makes possible the functional-programming paradigm.

<br>

- **Dynamically typed**

  In JavaScript, we don't assign data types to variables, they only become known when the JavaScript engine executes the code.

  Also, the type of variables can be changed as we reassign new values.

  Most other programming languages, have to manually assign types to variables, which may prevent bugs.

  If we want JavaScript with Types, we can try TypeScript.

<br>

- **Single-threaded, non-blocking event loop concurrency model**

  _Concurrency model_ refers to how the JavaScript engine handles multiple tasks happening at the same time.

  JavaScript itself runs in one _single-thread_, so it can only do one thing at a time.

  The _thread_ is where our code is executed in a machine's processor.

  In a long-running task, like fetching data from a remote server, the single thread code may get blocked. To avoid this, we want the so-called _non-blocking_ behavior, by using an _event loop_.

  The event loop take long-running tasks, executes them in the background, and then puts them back in the main thread once they are finished.

<br>

## JavaScript Over Time

- **1994** The NetScape web browser was launched.

- **1995**: Brendan Eich (from NetScape), created the very first version of JavaScript in just 10 days. It was called Mocha, but already had many fundamental features of modern JavaScript. Microsoft created IE web browser.

- **1996:** Mocha changes to LiveScript and then to JavaScript, in order to attract Java developers. However, JavaScript has almost nothing to do with Java. Opera web browser was launched.

  Microsoft copied JavaScript from Netscape and called it JScript. Netscape submitted JavaScript to a standards developing organization called Ecma International.

- **1997:** Ecma International released ECMA-262 which sets standards for the first version of the scripting language called ECMAScript 1, shortened ES1. This is the first official standard for JavsScript (ECMAScript is the standard, JavaScript is the language in practice).

  The new ECMAScript standard provided rules for the architecture of JavaScript new features, creating consistency between new and old JS versions.

- **1998** ES2 released. Mozilla Firefox was launched.

- **1999** ES3 was released (regular expressions, try-catch statements).

- **2000 - 2008** The release of ECMAScript 4 (ES4) was abandoned due to differences in committee opinions. During this time: Firefox, Apple Safari, Google Chrome were introduced. HTML5 was released.

- **2009** ES5 (ECMAScript 5) is released with lots of great new features (strict mode, JSON support, methods for strings and arrays). Node.js is launced (JS execution outside the browser).

- **2010** AngularJS framework was released.

- **2011** ES5.1 was released.

- **2013** React.js library and Electron.js framework was released.

- **2014** Vue.js framework was released.

- **2015** ES6 (ES2015 / ECMAScript 2015) was released. The biggest update to the language ever. ECMAScript changes to an annual release cycle in order to ship less features per update. Starting with ES6, is what we call modern JS because of the major additions.

  let and const, arrow functions, classes, parameters with default values, promises for asynchronous actions, array methods, and more.

- **2016 - present** Releases of ES2016, ES2017, ES2018, ES2019, etc.

<br>

### JavaScript is backward compatible up to ES1

- JavaScript engine that is in our browsers today is able to understand old code written 25 years ago, without having to repy on version numbers.
- It works this way because of the fundamental principle that is baked into the JavaScript language and its development, which is: **to not break the web**.
- This means that there is almost never anything removed from the language, but only added in new releases, so websites keep working.
- This comes with old bugs and weird things in the language, because as we know the very first version of JavaScript was made in just 10 days, and no one back then could even imagine what JavaScript would be used for one day. The initial goal of JS was just to add some simple dynamics to pages, not to write whole web applications in browsers like we do today.
- Anyway, we can go around many of this weird stuff by simply using the modern JavaScript that matters today and just ignore most of the old weird stuff.
- JavaScript is not forward compatible, current browsers do not understand code from the future.

<br>

### How we use modern JavaScript today

Considering that browsers that users are using might be old, and there's no forward compatibility, we need to consider 2 distinct scenarios: _development_ and _production_:

- The _development phase_ is when we're building the website on our computer. To ensure that we use the latest JavaScript features, we should use the most up to date version of Google Chrome browser.
- _Production_ is when our web app is finished, you deploy it on internet, and it's then running in your users' browser. The problem here is that the users could use old browsers which doesn't support the latest JS features. The solution to this problem is to convert the modern JS version back to ES5 using a process called transpiling and also polyfilling - with a tool called Babel, which transpile the code. We do transpiling back to ES5 only when the app is developed and ready to be deployed on internet.

ES5 is safe to be used as a target for transpiling, as it is supported in all browsers today.

Generally, newer releases are well supported in all modern browsers. Information about what features are currently supported and in which browsers: [ES6 Compatibility Table](https://kangax.github.io/compat-table/es6/). Future releases, all together are called ESNext.

Most browsers start implementing new features even before they enter the official ECMAScript specification. As new features are proposed, they have to go through four stages. Starting with stage one where the feature first is admitted, all the way to stage four at which point the feature enter the language officially. But when a feature is at stage three, browsers can be pretty sure it will eventually pass to stage four, and so they're gonna start implementing that feature while still in stage three.

<br>
<br>
<br>
