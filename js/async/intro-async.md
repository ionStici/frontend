[&larr; Back](./README.md)

# Introduction to Asynchronous Code

## Table of Content

- [General Asynchronous Programming Concepts](#general-asynchronous-programming-concepts)
- [Introduction to Asynchronous JavaScript](#introduction-to-asynchronous-javascript)
- [Synchronous vs Asynchronous Code](#synchronous-vs-asynchronous-code)

<br>

## General Asynchronous Programming Concepts

- **Synchronous code** executes in sequential order, line by line from top to bottom of the file. This type of behavior is known as _blocking code_ since each line of code cannot execute until the previous line finishes.

- **Asynchronous code** can be executed in parallel to other code that is already running, saving time and boosting efficiency. This type of behavior is considered _non-blocking_.

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

<br><br>

<hr>

<br><br>

[&larr; Back](./README.md)

## Synchronous vs Asynchronous Code

### Table of Content

- [Synchronous Code](#synchronous-code)
- [Asynchronous Code](#asynchronous-code)
- [Ajax and APIs](#ajax-and-apis)

<br>

## Synchronous Code

**Synchronous Code** is executed line by line, in the exact order of execution that we define in our code. Each line of code waits for the previous line to finish its execution, all in sequence.

The **Execution Thread** (part of the execution context) executes code in the computer's processor.

Synchronous code can create problems when one line of code takes too much time to run.

**Example:** the alert statement will create an alert window which will block the code execution until we click the 'ok' button.

<br>

## Asynchronous Code

```js
console.log("Hello");
SetTimeout(() => console.log("Async"), 1000);
console.log("World");
// Output: "Hello" -> "World" -> "Async"
```

The `setTimeout` function will start a timer in a asynchronous way. The timer will run in the background without blocking the code execution.

A callback function is registered and will execute only after the timer has finished running. _This callback function is asynchronous JavaScript_, because it will execute after a task that is running in the background (the timer).

So, the callback is registered and then we immediately move on to the next line. The code execution is not blocked. This is called **non-blocking** behavior.

When the timer finishes, the callback is executed as well. The callback will run after all the other code even though in the code it doesn't appear at the end.

_Asynchronous programming_ is all about coordianting the behavior of our program over a certain period of time (not occurring at the same time).

Callbacks has nothing to do with asynchronous code, only certain functions like `setTimeout` work in an asynchronous way.

### Loading an image

```js
const img = document.querySelector("img");
img.src = "img.jpg";
img.addEventListener("load", () => img.classList.add("fadeIn"));
```

Setting the `src` attribute of an image in JS happens asynchronously - loading an image in the background while the rest of the code can keep running.

Why this works like this? Imagine that it is a huge image, the entire code would wait for the image to load.

Once the image finished loading, the `load` event will automatically be emitted by JavaScript.

All this happens asynchronously in a non-blocking behavior.

What makes our code example asynchronous is the fact that the image is loading asynchronously in the background, and not the fact that we are listening for the load event.

Other examples of asynchronous code in JavaScript: the Geolocation API, Ajax calls.

Ajax calls are the most important use case of asynchronous code.

<br>

## Ajax and APIs

### Ajax

**Ajax** stands for **Asynchronous JavaScript And XML**.

It allow us to communicate with remote web servers in an asynchronous way.

With **Ajax calls** we can **request data** from web servers dynamically (without reloading the page).

Using Ajax, we can do an HTTP request to the server which will send back a response, containing the data we requested.

This request between **Client** and **Server** happens asynchronously in the background. There can be different types of requests, like GET or POST.

When we ask the server to give us data, the server usually contains a web API that takes the data and sends it back.

**API data format:** XML is a data format that was once used to transmit data on the web, nowadays no API uses XML data anymore. The term Ajax is just an old name that got very popular and so it's still in use today. Instead, most APIs use the **JSON** data format. JSON is basically just a JS object, but converted to a string. This makes it easy to send across the web and to use it in JavaScript once the data arrives.

<br>

### API

**API (Application Programming Interface):** a piece of software that can be used by another piece of software, in order to allow applications to talt to each other and exchange information.

This is true not only for web development, but for programming in general. In JavaScript and web development, there are countless APIs, examples: DOM API, Geolocation API, Own Class APIs, etc. They are called APIs, because they are self contained pieces of software that allow other pieces of software to interact with them.

We can implement a small and simple API in a Class, where we make some methods available as a public interface. Objects created from a class can be seen as self-contained, encapsulated pieces of software, that other pieces of software can interact with. This fits the definition of API.

An API is essentially an application running on a web server which receives requests for data, then it retrieves this data from some database and sends it back to the client.

Building APIs envolves backend development, so working with servers and databases.

As frontend developers, we are focusing in using third-party APIs that other developers have made available to us, most of the time for free.

Imagine we are building a traveling application. We have a database with different destinations and tours that we're offering. So we build our API on our server which receives requests from the frontend (client) and send back the results. This alone would probably not be enough to build a complete application. We can make our job easier using third-party APIs. THere are APIs for everything: to get wheather data for our destinations, data about countries, flights data, currency conversion data, APis for sending email or SMS, google maps, etc. APIs is what made the modern web.

<br>
