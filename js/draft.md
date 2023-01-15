# JavaScript Runtime Environments

A **runtime environment** is where your program will be executed.

JavaScript code may be executed in one of two runtime environments:

1. A browser's runtime environment
2. The Node runtime environment.

In each of these environments, different data values and functions are available, and these differences help distinguish front-end applications from back-end applications.

## The Browser Runtime Environment

Applications executed in the browser are known as fronend applications.

For a long time, JS code could only be executed in a browser and was used exclusively for creating frontend applications.

To create a backend application that could run on a computer without a browser, you would need to use other programming language.

<br>

## The Node Runtime Environment

In 2009, the Node runtime environment was created for the purpose of executing JavaScript code outside the browser, enabling programmers to create full-stack applications using only JavaScript.

Node runtime environment gives backend applications access to a variety of features unavailable in a browser, such as access to the server's file system, database, and network. At the same time, JavaScript in Node no longer has the features that were provided by the browser, such as APIs, the window object, etc.

## Recap

- Front-end JavaScript applications are executed in a browser’s runtime environment and have access to the window object.
- Back-end JavaScript applications are executed in the Node runtime environment and have access to the file system, databases, and networks attached to the server.

## Node

**Node.js** is a JavaScript runtime, or an environment which runs JavaScript code outside of the browser.

A **runtime** converts code written in a high-level programming language and compiles it down to code the computer can execute (machine code).

Node was created with the goal of building web servers and web applications in JavaScript, but it’s a powerful and flexible environment that can be used for building all sorts of applications.

Install Node bersion labeled "LTS" [nodejs.org](https://nodejs.org/en/)

In the terminal, `which node` will print the file path to Node. And `node -v` will print the version of Node.

## Use Node to Run Your Program

Navigate to your JavaScript file through the terminal, and run:

```
node fileName.js
```
