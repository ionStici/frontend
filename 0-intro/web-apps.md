# **Web Apps**

## **Table of Content**

- [Web Applications](#web-applications)
- [The Difference between Website and Web application](#the-difference-between-website-and-web-application)
- [Web Application Architecture](#web-application-architecture)
- [Single Page Application SPA Intro](#single-page-application-spa-intro)
  - [Multi-Page Applications](#multi-page-applications)
  - [Single-Page Applications](#single-page-applications)

<br>

## **Web Applications**

A web application is an application software that does not require installation and can instead be accessed from a remove server via a web browser.

Web applications are made for interaction, allowing users to send and consume data between the browser and the web server.

<br>

## **The Difference between Website and Web application**

A **website** can be defined as pages of content accessed through a web browser.

A web application is an application software that runs on a web server and is accessed by the user through a web browser (**focus on interaction with the user**).

Web applications are significantly more complicated than static websites (complex architecture and features).

<br>

## **Web Application Architecture**

In order to facilitate this complex flow of data, web applications are usually designed with different layers. The most common design paradigm is a three-layered design consisting of a presentation layer (web browser), application layer (server), and storage layer (database). In this system, the presentation layer is responsible for relaying user data to the application layer, which can process that data and do any number of things, including passing it to the storage layer for “safe-keeping.”

Many times, web applications can grow to be very complex. In these cases, a three-layered design may fall short. This may necessitate the introduction of additional layers to handle this complexity. For instance, the introduction of an integration layer between the application and storage layers can help provide a uniform interface for data access, allowing the application layer to be insulated from changes that occur to the storage layer implementation.

<br>

## **Single Page Application SPA Intro**

SPA combine the content of traditional websites with the smooth user experience of mobile applications.

### **Multi-Page Applications**

Website with multi-page file structure which lives on a server - each time new data is needed for the browser view, a request is sent to the server, which returns a new set of page files. This approach struggle to keep up with web apps.

The solution: Single-Page Applications.

### **Single-Page Applications**

A web application that interacts with the web browser by dynamically rewriting the current web page with new data from a web server, instead of the default method of the browser loading entire new pages.

The name single-page application generally refers to the application consisting of one page that is constantly updated by JavaScript.

Requests to the server are now quicker since they contain just the data needed to update the view. SPAs are full applications, running in the browser yet still connected to a server to update any application data.
