# **Web Apps**

## **Table of Content**

- [Web Applications](#web-applications)
- [The Difference between Website and Web application](#the-difference-between-website-and-web-application)
- [Web Application Architecture](#web-application-architecture)
- [Single Page Application SPA Intro](#single-page-application-spa-intro)
  - [Multi-Page Applications](#multi-page-applications)
  - [Single-Page Applications](#single-page-applications)
  - [SPA Frameworks](#spa-frameworks)
  - [SPA Pros and Cons](#spa-pros-and-cons)

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

Website with multi-page file structure which lives on a server - each time new data is needed for the browser view, a request is sent to the server, which returns a new set of page files. This approach struggle to keep up with modern web apps.

The solution: Single-Page Applications.

### **Single-Page Applications**

A web application that interacts with the web browser by dynamically rewriting the current web page with new data from a web server, instead of the default method of the browser loading entire new pages.

The name single-page application generally refers to the application consisting of one page that is constantly updated by JavaScript.

Requests to the server are quicker since they contain just the data needed to update the view. SPAs are full applications, running in the browser yet still connected to a server to update any application data.

Each interaction with the web app changes only parts of the HTML file, instead of the whole page. The file stays constant while the logic from the client-side changes only what is needed to update.

Requests for data are a lot quicker than requests for whole files.

SPAs focus on speed when it comes to user interaction and browser rendering times.

### **SPA Frameworks**

Frameworks are recommended for creating SPAs instead of only vanilla JavaScript.

- [React](https://reactjs.org/)
- [Vue.js](https://vuejs.org/)
- [AngularJS](https://angular.io/)
- [Ember.js](https://emberjs.com/)
- [ExtJS](https://www.sencha.com/products/extjs/)
- [Knockout.js](https://knockoutjs.com/)
- [Meteor.js](https://www.meteor.com/)

While all of these share similar goals, they each take different approaches to building SPAs.

### **SPA Pros and Cons**

Single-page applications provide a better user experience while running within a web browser. They are the right choice for applications that need to provide real-time or complex interaction with their users. Creating a SPA involves more than just a handful of HTML, CSS, and JavaScript files, but their complexity continues to be minimized by frameworks such as React and Vue.js.

#### **Pros**

- SPAs are fast, it feels like a desktop of mobile app, no requests for new files, only small amounts of data sent from the server.

- Reuse of code, saves time.

- SPAs provide an easier path to migrate code to a mobile application.

#### **Cons**

- SPAs require more files to run at startup so the load time of the application can be longer.

- Search Engine Optimization (SEO) has some pitfalls when it comes to SPAs. Search engines, like Google or DuckDuckGo, index pages of a website to rank the content. This can be difficult with only one page that may not have content until it is loaded by JavaScript. SEO is an ever-changing world so strategies already exist to mitigate these downsides.

- SPAs may not function as expected within the browser. For example, the back button or browsing history can act differently while using a single-page application. This can be frustrating for users who are expecting certain functionality within their browsers.
