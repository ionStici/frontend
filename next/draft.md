# Draft

NextJS helps with building fullstack React apps, by pre-rendering pages on the server-side (SSR).

NextJS Data Fetch / blending client-side and server-side code.

Statis vs Server-side page generation.

<br>

## The Problem With Traditional React Apps (and Data Fetching)

In traditional React Apps, initially we get an empty html document with a single `div`, then the JS bundle will render the content and components in that `div`, this may lead to delay in website rendering, especially if first we need to fetch some data that must to be rendered, bad UX.

Besides that, search engines have no way of inspecting the website content, which leads to bad SEO indexing.

<br>

## How NextJS Prepares & Pre-renders Pages

NextJS sends back a pre-rendered page.

When a request is made to a website built with NextJS, it returns a pre-rendered page.

Instead of loading data only after the page was sent back to the client, NextJS pre-renderes the page, so the html document with all the data that might be needed, it loads that in advance and pre-generates the finished html page, so that it's this finished html page that can be sent back to the client. Good for SEO.

But also it will send the JS script, by a process named Hydrating

The JS script will be send as well, NextJS will hydrate with React code once loaded, this will lead to the fact that the JavaScript code will take over the pre-rendered page and let React do its job, by this we still have an interactive app.

It sent back the pre-rendered page so that all the core content was already there right from the start, and so that search engines could see the content.

So, NextJS prepares a page in advance, pre-building all the html content, and by pre-loading all the data that will eventually be needed.

Note: this pre-rendering only affects the initial load. Once we are on a website powered by nextJS and React, and once the page is hydrated which happenes right after this pre-rendering, then we have a single-page-application again, then React takes over and handles everything on the frontend. If we visit another page of our website, then that page is not pre-rendered, but instead created in the client by React, only the initial page visit is pre-rendered, so that we don't get the empty page until React is ready.

_NextJS has 2 forms of pre-rendering which you can choose from:_

1.  Static Generation **(Recommended)**
2.  Server-side Rendering

_Main difference:_

with static generation all the pages are pre-generated in advance in the build phase. So when you build you app for production before you deploy it, you prepare all those pages.

With server-side rendering, pages are created just in time after deploymen when a request reaches the server.

There are ways of mixing that.

<br>

## Static Generation with "getStaticProps"

**Static Generation:** pre-generate a page during build time. "Pre-generate a page" means that all html code and all data that makes up the content is prepare in advanced, during the build process where you are allowed to execute code that would normally only run on the server-side.

Again, data and pages are prepared during build-time, when you build your app, before you deploy it. Because pages are pre-build during build time, once you deploy them, they can be cached by the server, therefore incoming requests can be served instantly with those pre-build pages.

After the pre-build pages are served, they are still hydrated with the React app. The point is the the pages sent to the client are not empty, but populated with content.

How do we tell NextJS that a certain page should be pre-generated?

ONLY from inside `pages/` folder components (not from React components) we can export the special function: `export async function getStaticProps(context) {}` - in this function we can run any code that would normally run on the server-side only. So in this function we don't run client-side code, and also we don't have access to certain client-specific features like the `window` object, but instead we can run any code we want that would normally run on the server-side. Code that we write in this `getStaticProps` function, will not be included in the code bundle that it is sent to the clients, code from here will never be seen by the clients. For example, if it contains code with database credentials, we can safely include them, because this code will never make to the client-side.

<br>

## NextJS Pre-renders By Default!

By default, NextJS pre-renders all pages that have no dynamic data.

<br>

## getStaticProps

`getStaticProps()` function can be added to any page file, and only there, you need to export it so that NextJS will call this function when it pre-generates a page.

This function signals (confirms) to NextJS that this is a page that should be pre-generated.

```js
// pages/index.js
function HomePage(props) {
  const { products } = props;
  // [ { id: "1", text: "Product 1" } ]

  return null;
}

export async function getStatisProps() {
  return {
    props: {
      product: [{ id: "1", text: "Product 1" }],
    },
  };
}

export default HomePage;
```

Pre-fetch data before the component is pre-rendered.

`getStaticProps()` function must return an object with a `props` key.

This function prepares the `props` for its component.

NextJS first executes `getStaticProps`, which prepares the props for the component function, and only then it will execute the component function.

In this `getStaticProps()` function we can run any code we want, code that will never be visible on the client-side, that fetches data, that exposes data, through `props` to the component.

So, the object with the `props` key that `getStaticProps` returns, will get passed to the actual page component through `props`, it does this in advance, so none of this will happen on the client-side, instead this happens during build time.

If we view the page source, we see that the data the component rendered is part of the page that was sent to the client. So fetching that data did not happen on the client, it happened on the server. Again, on the client-side, we would not find the code from `getStaticProps` anywhere, it's not part of the client-side code. This means that the code from `getStaticProps` can do server-side things, for credentials, for code that would not work in the browser.

<br>

## Running Server-side Code & Using the Filesystem

Any code inside `getStaticProps` is executed on the server-side, this means that we now can work with the file-system.

Import the `fs` node.js core module. Working with `fs` would fail if we would try to work on the client-side, browser-side JavaScript can't access the file-system.

We can use the `fs` **file-system** module inside the `getStaticProps` function.

NextJS will split the code in a clever way so that imports like `fs` and functions like `getStaticProps` will not make to the final client-side bundle.

We can use `fs` to get access to files from the project directory, using the `fs.readFileSync()` function, which synchronously reads the file and blocks the execution until it's done. `readFile` on the other hand expects a callback.

`import fs from "fs/promises"` this is a special version of `fs` module that uses promises. When we do so, `fs.readFile()` returns a promise. Now we can just specify the file path and `await` for it, for the data.

The `path` nodejs module contains helpful functionalities for building paths.

Using `path.join()`, it will build a path that will be consumed by `fs.readFile()`.

`process.cwd()` nodejs object gives the current working directory, so the root. So using this, we tell `path.join()` to start from the root directory, then the following arguments are the paths to the data we are looking for.

```js
import path from "path";
import fs from "fs/promises";

function HomePage(props) {
  const { products } = props;

  return null;
}

export async function getStaticProps() {
  const filePath = path.join(process.cwd(), "data", "dummy-backend.json");
  const jsonData = await fs.readFile(filePath);
  const data = JSON.parse(jsonData);

  return {
    props: { products: data.products },
  };
}
```

<br>

## A Look Behind The Scenes

The `build` nextjs script will create the optimized production-ready build, it's this step which pre-generates our pages.

In the terminal we get information about the build it created, about the static pages it generated.

The output of `build` script, so the production ready code is in the `.next` folder.

`.next/server/pages/index.html`

The `start` script will start the production ready page with a nodejs server.

<br>

## Incremental Static Generation (ISR)

When we say that `getStaticProps()` executes code on the server-side that's partially correct, we can execute server-side code here but in the end this code will not run on the actual server which serves our application, instead it runs on our machine in the build process, when we run the `build` script and next.js does its job.

Now, what to do if we have data that changes frequently? instead of static data with pre-generated pages, like a blog where data doesn't change too often.

What if we need to add some more data after the page was deployed? We need to re-build and re-deploy the page all the time, in case we use `getStaticProps`.

- ONE solution would be: `useEffect` for fetching data from a server.

- A BETTER solution would be:

The `getStaticProps()` function executes when we run the `build` script, but..

Next.js built-in feature: **Incremental Static Generation**, it means that we don't generate our page statically once at build time, but that it's continuously updated even after deployment without you re-deploying it.

So, we pre-generate a page, but then, we tell next.js that a given page should be re-generated again for every incoming request at most every X seconds.

So, we have ongoing pre-rendering on the server for incoming requests. For this, we pass the second key to the returned object of `getStaticProps` by the name `revalidate`, and the value must be a number that represents the time in seconds that NextJS should wait until it should re-generated the page.

```js
export async function getStaticProps() {
  //

  return {
    props: {
      //
    },
    revalidate: 10, //
  };
}
```

BTW, during development, the page will be re-generated for every request, the `revalidate` time matters for production.

<br>
