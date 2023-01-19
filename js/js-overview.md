[&larr; Back](./README.md)

# JavaScript Overview

## Table of Content

- [JavaScript Introduction](#javascript-introduction)
- [JavaScript Definition](#javascript-definition)
- [JavaScript Over Time](#javascript-over-time)

<br>

## JavaScript Introduction

**JavaScript** is the programming language of the web.

- Build web apps in the browser, load data from remote servers.
- Add dynamic and interactive effects to any webpage, manipulate content or CSS styles.
- JavaScript be used in both the frontend and backend of web development.

- It is frequently updated with new versions.
- JS integrates easily with HTML and CSS. - manipulate content or the CSS styles.
- JS allow websites to have interactivity
- JS offers a wide range of frameworks and libraries for complex applications with low overhead.

JavaScript used for servers (server-side JavaScript)

JS can be integrated with other languages to communicate with databases.

Node.JS, or Node, is one of the most popular versions of server-side JavaScript. Node has been used to write large platforms for NASA, eBay and many others. Since Javascript can execute programs out of sequential order, Node can be used to create scalable web applications, messaging platforms, and multiplayer games. This is why Google Cloud and Amazon Web Service depend on Node for some of their services.

Beyond the web, JavaScript has a large presence amongst cross-platform applications. We use some popular standalone desktop apps like Slack, GitHub, Skype, and Tidal. These applications are developed with the JavaScript framework called Electron.js. Electron is excellent for making desktop applications that need to work across different devices regardless of operating system.

In addition, JavaScript has the potential of expanding into other innovative technologies such as virtual reality and gaming. JavaScript can be used for animating, rendering and scaling. JavaScript even has contributed to the internet of things, the technology that makes simple objects, like your fridge, smarter. Everyday devices can become interactive and collect data using JavaScript libraries.

JS libraries - consists of functions that an application can call to perform a task.

JS frameworks - defines how a developer design an application.

All these frameworks and libraries are 100% based on JavaScript, so you have to become really good at JS before learning and using any of these tools.

The JavaScript language and the web browsers are 2 separate things. JS can also run outside of web browsers, for example on a web server, using node.js technology. This allows us to create back-end applications, which run on a web server and interact with databases. When we use JS in the browser, we create front-end applications.

We also can use JS to build native mobile and desktop applications, for any phone and computer system. This is due to modern tools like React Native, Ionic frameworks, Electron tool.

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

- **1996:** Microsoft copied JavaScript from Netscape and called it JScript. Netscape submitted JavaScript to a standards developing organization called Ecma International.

- **1997:** Ecma International released ECMA-262 which sets standards for the first version of the scripting language called ECMAScript 1, shortened ES1. This is the first official standard for JavsScript (ECMAScript is the standard, JavaScript is the language in practice).

  The new ECMAScript standards provided rules for the architecture of JavaScript new features, creating consistency between new and old JS versions.

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
