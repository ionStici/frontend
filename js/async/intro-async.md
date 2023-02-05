[&larr; Back](./README.md)

# Introduction to Asynchronous Code

## Table of Content

- [General Asynchronous Programming Concepts](#general-asynchronous-programming-concepts)
- [Introduction to Asynchronous JavaScript](#introduction-to-asynchronous-javascript)
- [Synchronous vs Asynchronous Code](#synchronous-vs-asynchronous-code)
- [Ajax and APIs](#ajax-and-apis)

<br>

## General Asynchronous Programming Concepts

- **Synchronous code** executes in sequential order, line by line from top to bottom of the file. This type of behavior is known as _blocking code_ since each line of code cannot execute until the previous line finishes.

- **Asynchronous code** can be executed in parallel to other code that is already running, saving time and boosting efficiency. This type of behavior is considered as _non-blocking_.

- **Asynchronous Code Under the Hood**

  For most programming languages, the ability to execute asynchronous code depends on the number of **threads** that the app has access to.

  We can think of a thread as a resource that a computer provides to an app to do a task (to run code). A thread per task.

  The more threads we have, the more tasks we can run concurrently.

  In most modern-day computers, multithreading is achieved by having a CPU that has multiple cores or by some other technology.

- **Asynchronous Code in Web Development:** loading only the code that is necessary for user interactions and then load up bits of code in the background.

  Asynchronous code in the browser creates a better user experience.

<br>

## Introduction to Asynchronous JavaScript

- JavaScript is a **single-threaded** language. It has a single thread for one task at a time.

  But, JavaScript has a runtime model based on an **event loop**, which allows it to perform asynchronous tasks even while only using a single thread.

- **Asynchronous callbacks**

  ```js
  btn.addEventListener("click", callback);
  ```

  The callback will execute after a specific condition is met and runs concurrently to any other code currently running.

- **`setTimeout()` and `setInterval()`**

  ```js
  setTimeout(() => callback, 1000);
  setInterval(() => callback, 1500);
  ```

  `setTimeout()` will execute the callback in a non-blocking way after the specified amount of time in milliseconds (second argument) has elapsed.

  `setInterval()` will execute its callback each X amount of time (second argument).

  Both built-in functons perform tasks asynchronously.

<br>

## Synchronous vs Asynchronous Code

## Synchronous Code

**Synchronous Code** is executed line by line, in the exact order of execution that we define in our code. Each line of code waits for the previous line to finish its execution, all in sequence.

The **Execution Thread** (part of the execution context) executes code in the computer's processor.

Synchronous code can create problems when one line of code takes too much time to run.

**Example:** the alert statement will create an alert window which will block the code execution until we click the 'ok' button.

## Asynchronous Code

```js
// EXAMPLE 1
console.log("Hello");
SetTimeout(() => console.log("Async"), 1000);
console.log("World");
// Output: "Hello" -> "World" -> "Async"

// EXAMPLE 2
const img = document.querySelector("img");
img.src = "img.jpg";
img.addEventListener("load", () => img.classList.add("fadeIn"));
```

- _Example 1 -_ The **`setTimeout`** function will start a timer in the background in an asynchronous way, without blocking the code execution (non-blocking behavior). The callback is registered and will execute only after the timer has finished running in the background, meanwhile the code moves on to the next line.

  This callback is _asynchronous JavaScript_ because it executes based on a task running asynchronously in the background (the timer). When the timer finishes, the callback will be placed in the call stack to execute. It will run after all other code, even though it doesn't appear at the end of code.

- _Example 2 -_ **Loading an Image:** Setting the `src` attribute of an image in JavaScript happens asynchronously. The image is loaded in the background whole the rest of the code can keep running. It was implemented this way because images can be large in terms of kilobytes, which can then block the code execution.

  Once the image finished loading, the `load` event will automatically be emitted by JavaScript. All this happens asynchronously and in a non-blocking behavior.

Callbacks and events have nothing to do asynchronous code, what makes our code examples asynchronous are the `setTimeout` function and the `src` attribute that loads images in the background.

<br>

## Ajax and APIs

- **Ajax** stands for **Asynchronous JavaScript And XML**.

  With **Ajax Calls** we can "communicate" and **request data** from remote servers asynchronously and dynamically (without reloading the page).

  Using Ajax, we can do HTTP requests to the server which will send back a response containing the data we requested. This request between the **Client** (browser) and the **Server** happens asynchronously.

  The server usually contains a **web API** that receives the request, retrieves the data, and sends it back.

  **API data format:** XML is a data format that was once used to transmit data on the web, nowadays no API uses XML data anymore. The term Ajax is just an old name that got very popular and so it's still in use today. Instead, most APIs use the **JSON** data format. JSON is a JavaScript object converted to a string.

<br>

- **API (Application Programming Interface):** a piece of software that can be used by another piece of software, in order to allow applications to talk to each other and exchange information.

  In web development there are countless APIs: DOM, Geolocation, our own Class APIs, etc. They are called APIs, because they are self contained pieces of software that allow other pieces of software to interact with them.

  We can implement a simple API in a Class, where we make some methods available as public interface. Objects created from a Class can be seen as self-contained and encapsulated pieces of software that other pieces of software can interact with - this fits the definition of API.

  An API is essentially an application running on a web server which receives requests for data, then it retrieves this data from some database and sends it back to the client. Building APIs envolves backend development (working with servers and databases). As frontend developers, we are focusing in using third-party APIs that other developers have made available to us, most of the time for free.

<br>
