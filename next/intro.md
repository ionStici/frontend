# Next.js

## Table of Content

- [What is Next.js](#what-is-nextjs)
- [1. Feature: Server-side Page (Pre-)Rendering](#1-feature-server-side-page-pre-rendering)
  - [SSR vs SSG](#ssr-vs-ssg)
- [2. Feature: File-based Routing](#2-feature-file-based-routing)
- [3. Feature: Build Fullstack React Apps](#3-feature-build-fullstack-react-apps)

<br>

## What is Next.js

**React** is a JS library (provides helpful functions) for building interactive **user interfaces**.

**Next.js** is a (_fullstack_) React **framework** that gives you building blocks to create web applications.

**Next.js** enhances **React** by adding additional core features.

<br>

## 1. Feature: Server-side Page (Pre-)Rendering

**Server-Side Rendering** - The page requested is rendered and filled on the server.

<br>

**Client-side Rendering** - If we take a look at the **Page Source** of a loaded React app, we see that all it contains is an empty `div` with a `root` id.

Within this `div`, React will render the entire application on the client-side.

Key Idea: the HTML document sent to the user from the server is initially empty.

Potential Problems of client-side rendering: not fast enough UX, lack of SEO.

<br>

**Server-side Rendering** - The page is pre-rendered on the server, then the complete page is served to the user and to search engines (faster & better SEO).

Next.js has built-in server-side rendering by default, it automatically pre-renders the pages, which is great for SEO and initial load experiences.

Even if Next.js pre-renders on the server, we still get a React application running in the browser.

<br>

### SSR vs SSG

- **Server-side Rendering (SSR)**

  - SSR is a rendering technique where the HTML of a page is generated on the server for each request.
  - Beneficial for SEO as Search Engine Crawlers can easily index the server-rendered content.
  - Faster **First Contentful Paint (FCP)** compared to **Client-Side Rendering (CSR)**.
  - SSR can be resource-intensive on the server.

- **Static Site Generation (SSG)**

  - SSG pre-generates "static" HTML pages once at build time, then these pages are used for every request, with no further processing on the server.
  - SSG is highly performant, it reduces the load on the server. The pre-generated pages can be served directly from a Content Delivery Network (CDN).
  - Beneficial for SEO as the pages are already rendered and can be easily crawled by search engines.

- **Differences between SSR and SSG**

  - _Rendering Time:_ SSR renders pages at runtime (when a user requests the page), while SSG renders pages at build time.
  - _Performance:_ SSG has better performance (the pages are pre-generated & served via CDN). SSR may have higher server load and latency as the server needs to render pages on-the-fly for each request.
  - _SEO:_ Both SSR and SSG are good for SEO as they generate fully-rendered pages that are easily indexable by search engines.
  - _Use Cases:_ SSR is used for dynamic apps where the content changes frequently. SSG is more suited for static or less dynamic content.

In Next.js we can use both SSR & SSG rendering methods within the same project, allowing for a highly optimized and flexible architecture.

**Latency:** time it takes for a request to go from the client to the server and back to the client.

<br>

## 2. Feature: File-based Routing

**File-based Routing** is a routing paradigm where the structure of your URLs is determined by the file structure of your `pages` directory.

A **Router** watches the URL, and if it changes, the router will prevent the browser's default behavior of sending a request, instead it will render a different react component on the page, giving the illusion that the page has changed.

With file-based routing we change what is visible on the screen based on the url, but without sending an extra request to a server.

Next.js provides a special `pages` folder where we can define the routes and paths using files and folders.

<br>
<br>
<br>
<br>
<br>

## 3. Feature: Build Fullstack React Apps

Backend Capabilities

NextJS makes it easy for us as a developer to add standalone backend code.

With NextJS is's easy to add our own backend SPI into our react project using Node JS code - this allows us to add code for storing data to a database or to files, getting data from these, adding authentification, etc.

We don't have to build a standalone Rest API project, instead we can work on one NextJS project with all the react code, and also blend in our backend API code.

<br>

# Creating a NextJS Project

1. must nodejs installed

2. `npx create-next-app@latest`

<br>

## About the "App Router"

Using "App Router" is an alternative to using "Pages Router".

App Router uses a different project structure and different features.

For example, in "App Router", server actions feature is still in alpha, feature which handles all non-get requests in a NextJS app.

If we want to build a NextJS app where data can change, where users can submit forms, we will need these server actions to handle these changes on the backend. This feature right now is not recommended for production.

Because of this, now we will use "Pages Router". Later we will check out "App Router" as well.

<br>

## Analyzing a NextJS App Directory

`pages` most important, file based routing, define the different pages that will make up the app.

`public` public resources

`styles` for css

In our NextJS app we don't have a html document as we would do in a react app, that's because NextJS has built-in pre-rendering, it gives you that single-page-application dynamically pre-rendered when the request reaches the server.

NextJS allows us to determine WHEN a page should be pre-rendered.

Execute: `npm run dev`

What we see on the page after live hosting, is the result of the `index.js` file from `pages` directory. This file contains a regular react component, but this component is actually now pre-rendered. In DevTools, we can see that all the html markup is in place, not just the `div` element with the `app` id.

NextJS key feature: Build in page pre-rendering.

<br>
