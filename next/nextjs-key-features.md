# NextJS Key Features

Next.js - the React Framework for Production (fullstack framework).

What is a Framework? (compared to a library) - bigger, more features, it gives clear rules on how you write code.

Next.js enhances React by adding additional core features.

Why production? Because next.js solves common problems related to production.

<br>

## Feature: Server-side Page (Pre-)Rendering

Server-side rendering - Preparing the content of a page on the server instead of on the client.

If we inspect the source code of a loaded react page, we notice that all it contains is a `div` with a `root` id.

This `div` element is the one in which all the react app is rendered, but since react is a client-side library, all the rendering happens on the client, not on the server.

This is that the HTML code sent to the user from the server is empty at start.

Potential problems of client rendering: not fast enough user experience, lack of SEO (search engines will not see the content, they see just an empty html).

Solution: Server-side rendering

The page is pre-rendered on the server, then the finished page is served to users and to search engines - no flickering loading state, and search engines would see the page content.

Server-side rendering - pre-render react component on a server.

Next.js has built-in server-side rendering by default, it automatically pre-renders your pages, which is great for SEO and initial load experiences.

With next.js after the initial load, we still get a react application running in the browser.

Client-side and Server-side code is kind of clended together with NextJS - fetch data on the server and render finished pages.

<br>

## Feature: File-based Routing

Routing - give the user the ilusion of having multiple pages.

A router watches the url and when it changes it prevents the browser default of sending a request to some backend server, and instead renders a different component on the page with react. We change what is visible on the screen based on the url without sending a extra request to a server.

With react, Routing is set up in code.

With NextJS, we define pages and routes with files and folders. In NextJS, we have a `pages` folder, then the structure of this folder defines the routes and paths the app supports. Less work than with React Router.

<br>

## Feature: Build Fullstack React Apps

Backend Capabilities

NextJS makes it easy for us as a developer to add standalone backend code.

With NextJS is's easy to add our own backend SPI into our react project using Node JS code - this allows us to add code for storing data to a database or to files, getting data from these, adding authentification, etc.

We don't have to build a standalone Rest API project, instead we can work on one NextJS project with all the react code, and also blend in our backend API code.

<br>
