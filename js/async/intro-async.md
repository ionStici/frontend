[&larr; Back](./README.md)

# Introduction to Asynchronous Code

## Table of Content

- [General Asynchronous Programming Concepts](#general-asynchronous-programming-concepts)
- [Introduction to Asynchronous JavaScript](#introduction-to-asynchronous-javascript)

<br>

## General Asynchronous Programming Concepts

- **Synchronous code** executes in sequential order, line by line from top to bottom of the file. This type of behavior is known as _blocking code_ since each line of code cannot execute until the previous line finishes.

- **Asynchronous code** can be executed in parallel to other code that is already running, saving time and boosting efciency. This type of behavior is considered _non-blocking_.

- **Asynchronous Code Under the Hood**

  For most programming languages, the ability to execute asynchronous code depends on the number of **threads** that the app has access to.

  We can think of a thread as a resource that a computer provides an app to do a task (to run code). A thread per task.

  The more threads we have, the more tasks we can run concurrently.

  In most modern-day computers, multithreading is achieved by having a CPU that has multiple cores or by some other technology.

- **Asynchronous Code in Web Development:** loading only the code that is necessary for user interactions and then load up bits of code in the background.

  Asynchronous code in the browser creates a better user experience and makes the applications more efficiently.

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
