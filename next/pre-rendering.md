# Page Pre-Rendering & Data Fetching

## Table of Content

- [Introduction](#introduction)
- [Static Site Generation & "getStaticProps"](#static-site-generation-with-getstaticprops)
- ["getStaticProps"](#getstaticprops)
- [Running Server-side Code](#running-server-side-code--using-the-filesystem)
- [Incremental Static Generation (ISR)](#incremental-static-generation-isr)
- [The "context" Argument](#the-context-argument)
- ["notFound" property](#notfound-property)
- ["redirect" property](#redirect-property)

<br>
 
## Introduction

In traditional React applications, the browser initially receives an empty html document with a single `div` tag in which the JavaScript bundle will render all the content and components. This may lead to delay in website rendering and poor SEO indexing.

With Next.js, on the other hand, the browser receives a pre-rendered version of the page from the server. Next.js prepares the page in advance by pre-building all the html content and by pre-loading all the data that will eventually be needed.

Even so, the JavaScript bundle is also sent, next.js will hydrate with React code once loaded, so that eventually React takes over the pre-rendered page.

**Consider:** Pre-rendering only affects the initial load, once the page is hydrated, which happenes right after pre-rendering, then we have a traditional single-page-application, React takes over and handles the frontend. If we visit another page of our website, that page is not pre-rendered, instead created on the client by React, only the initial page visit is pre-rendered so that we don't get an empty page until React is ready.

<br>

**Page Pre-Rendering** - generating the HTML for a page in advance, instead of having it all done by the client-side JavaScript.

Next.js has two forms of pre-rendering: **Static-site Generation (SSG)** and **Server-side Rendering (SSR)**

- SSG is when the HTML is generated in advance at build time (before deployment) and will be reused (the html) on each request.

- SSR is when the HTML is generated on each server request (after deployment).

We can mix SSG and SSR. Pre-rendering ensures that your SPA is indexed properly by search engines, and also it can improve performance.

<br>

**Data Fetching** - retrieving data from a backend for your page.

- For SSG, next.js provides the `getStaticProps` function to fetch data at build time.

- For SSR, next.js provides the `getServerSideProps` function to fetch data on each request.

- Next.js also provides the `getStaticPaths` function, used for dynamic routes, which lets you specify which paths you want to pre-render.

These data fetching methods run on the server-side, meaning they do not send any client-side JavaScript to the browser that would affect the SEO of the page.

<br>

Together, these concepts allow you to build _performant, SEO-friendly, data-rich applications_ using Next.js and React.

<br>

## Static Site Generation with "getStaticProps"

**Static Site Generation** - Pre-generate pages (HTML and data) during the **build process**.

After deployment, these pre-generated pages are served instantly for incoming requests. These pre-generated pages once served are still hydrated with React. The idea is that the pages sent to the client are not empty, but populated with content.

`getStaticProps` provides a server-side data fetching mechanism that operates at build time, enabling you to generate static, SEO-friendly, and highly optimized pages that load quickly and provide a great user experience.

- **Build-Time Execution**

  After `next build`, the `getStaticProps` functions in your pages are executed on the server-side during this build process. This is where the data-fetching happens.

- **Server-side Context**

  While `getStaticProps` operates at build time, it runs in a Node.js environment, which is a server-side context. This means you have access to server-side functionalities like connecting to a database, accessing the file system, making HTTP requests to external APIs, and more.

- **Generation of Static HTML**

  The data fetched by `getStaticProps` is used to generated static HTML for each page. This static HTML, along with the fetched data, is saved and later served from a CDN for each incoming request to that page.

- **Client-side Hydration**

  Once the static HTML reaches the client (browser), Next.js "hydrates" the page to add interactivity using React. The data fetched by `getStaticProps` is passed as props to your page component, enabling you to use this data for rendering.

- **Separation of Concerns**

This setup allows for a clean separation of concerns: Server-side operations (like data fetching) happen in `getStaticProps`, whilc client-side rendering and interactivity are handled by your page component.

_How to pre-generate a page?_ Next.js pre-generates pages by default. To implicitly indicate that a page should be pre-generated, just include the `getStaticProps` function.

The `getStaticProps` function can be used only in `pages/` files. In this function we can run any code that would normally run on the server-side only (Node.js Runtime Environment). So, in this function we don't run client-side code, we don't have access to certain client-specific features like the `window` object. Code that we write in `getStaticProps` will not be included in the bundle sent to the browser, we can safely include database credentials in here.

<br>

## "getStaticProps"

`getStaticProps` function can be added to any page file, and only there. You need to export it so that Next.js will call it when it pre-generates the page. This function confirms to Next.js that this page should be pre-generated.

```js
// pages/index.js

export default function HomePage(props) {
  const { data } = props;

  return <h1>Hello World!</h1>;
}

export async function getStaticProps(context) {
  const response = await fetch("api");
  const data = response.json();

  return {
    props: {
      data,
    },
  };
}
```

`getStaticProps` must return an object with a `props` key.

1. `getStaticProps` runs at build time on the server-side
2. It fetches data before the component is pre-rendered
3. Then passes that data as `props` to the page component
4. Then the page component will render, accessing that data through props

None of this happens on the client-side, but during the build process, in a node.js environment.

If we view the Page Source, we can see that the HTML document is filled, so fetching the data did not happen on the client, but on the server.

The `next build` script will create the optimized production-ready build, it's this step which pre-generates the pages. In the terminal we get information about the static pages it generated.

The output of `next build` can be found in `.next/server/pages/index.html`

The `next start` script will start the production ready page with a node.js server.

<br>

## Running Server-side Code & Using the Filesystem

```js
import path from "path";
import fs from "fs/promises";

export default function HomePage(props) {
  const { data } = props;

  return null;
}

export async function getStaticProps() {
  const filePath = path.join(process.cwd(), "data", "todos.json");
  const jsonData = await fs.readFile(filePath);
  const data = JSON.parse(jsonData);

  return { props: { data } };
}
```

Code inside the `getStaticProps` function is executed on the server-side in a Node.js environment, we can use Node.js core modules in here, this means that we can work with the file-system.

Next.js will split our code in a clever way so that imports like `fs` and functions like `getStaticProps` will not make to the final client-side bundle.

The `fs` module from `"fs/promises"` is a special version of the `fs` module that uses promises. Now, `fs.readFile()` will return a promise, so we have to `await` for the response.

The `path` node.js module contains helpful functionalities for building paths. Using `path.join()` we can build a path that will be consumed by `fs.readFile()`

`process.cwd()` node.js object gives the current working directory, the root. This object will tell `path.join()` to start from the root directory, then the following arguments are the paths to the data we are looking for.

<br>

## Incremental Static Generation (ISR)

Next.js mechanism to provide fresh content with a static-site generation approch.

```js
export async function getStaticProps() {
  const data = "...";

  return {
    props: { data },
    revalidate: 10, // Re-generate the page every 10 seconds
  };
}
```

Code from `getStaticProps` executes on the server-side, but not on an actual server which serves the application, instead it runs on our machine in the build process when we run `next build`.

What to do if data changes frequently? Re-build & Re-deploy all the time? Or maybe `useEffect`?

Even if `getStaticProps` function executes when we run the `build` script, we can continuously update the page after deployment without re-deploying, using a Next.js built-in feature:

**Incremental Static Generation** allows you to update static pages after they have been generated, on a per-page basis, without needing to rebuild the entire site.

Specify a `revalidate` period in seconds, this tells next.js how often to regenerate a given page.

### Regeneration Process

When a request is made to a page, Next.js will check the revalidation period.

If the page is "stale" (older than the revalidation period), Next.js will server the stale page to the user for a faster response, while triggering a regeneration process on the server.

The regeneration process involves executing `getStaticProps` function again on the server to fetch the latest data and generate a new version of the page.

Once the regeneration process is complete, the newly generated page replaces the old (stale) page in the cache. Subsequent requests from users will receive the update page until it becomes stale again, at which point the process repeats.

Regeneration occurs on the server-side when a stale page is requested, allowing for the page to be update without blocking user requests. The client-side is not involved in the regeneration process, it merely receives the potentially stale page.

<br>

## The "context" Argument

The `getStaticProps(context)` function when called by Next.js, receives a `context` object argument.

```js
export async function getStaticProps(context) {}
```

`context` is an object with extra information about the page when the function is executed, it holds dynamic params, dynamic path segment values, and more.

<br>

## "notFound" property

```js
export async function getStaticProps() {
  // ... data fetching

  if (!data) {
    // if data is not found, return 404 error
    return {
      notFound: true,
    };
  }

  return {
    // otherwise, return the data as a prop
    props: { data },
  };
}
```

The `notFound` key when set to `true`, the page will return a `404` error, therefore `404.html` will render.

<br>

## "redirect" property

`redirect` the user to another page

```js
export async function getStaticProps() {
  // ... data fetching

  if (!data) {
    // if data is not found, redirect to another page
    return {
      redirect: {
        destination: "/no-data",
        permanent: false, // This redirection is not permanent
      },
    };
  }

  // otherwise, return data to props
  return {
    props: { data },
  };
}
```

If no `data`, then `redirect` the page to `no-data` route instead of this current page.

- `destination` - the url to redirect to.

- `permanent` - a boolean indicating whether the redirection is permanent `true` or temporary `false`. A permanent redirect will signal search engines to update their indexes with the new URL.

<br>
<br>
<br>
<br>
<br>

<!-- ## Working with Dynamic Parameters

Extracting `params` in the component function using `useRouter`, we work with params in the browser.

For pre-rendering a page, where we prepare the data for pre-rendering the page, then this happens on the server, for example using `getStaticProps` which runs before the component function runs.

We can use the `context` object that `getStaticProps` receives to work and get access to `params` (to the dynamic path segment) inside this pre-generating function, so that we could prepare the data for the component before it runs. Then we don't need to extract that dynamic segment in the component function.

### "getStaticPaths" For Dynamic Pages

If we have a dynamic page with square brackets `[id].js` then the default behavior is not to pre-generate the page with `getStaticProps`, because technically we will have multiple pages with different data, next.js doesn't know in advance how many pages to generate. Instead, these pages are always generated just in time on the server. Now it doesn't work because we added `getStaticProps`.

When we add `getStaticProps()` functionw to a page component file, then we tell next.js that you want to pre-render the page in advance.

For dynamic routes we need to give next.js more information. We can tell next.js which paths of a dynamic page should be pre-generated. For example we can tell next.hs which ids this route `[id].js` expects, so that it will pre-generate.

So that in the end, multiple pages could be pre-generated by next.js by knowing the pages in the first place.

We can inform next.js about this with another function: `export async function getStaticPaths() {}` , this is also a function that we can add only to `pages` component functions. And also we need to export it to make next.js aware of it.

### getStaticPaths

The goal of `getStaticPaths` function is to tell next.js which instances of this dynamic page `[id].js` should be generated.

```js
export async function getStaticPaths() {
  return {
    paths: [
      { params: { pid: "p1" } },
      { params: { pid: "p2" } },
      { params: { pid: "p3" } },
    ],
    fallback: false,
  };
}
```

This tells next.js that the dynamic page that contains the above `getStaticPaths` function, should be pre-generated 3 times with those 3 values `p1 p2 p3`.

THEN, next.js will call `getStaticProps` 3 times for these different ids, and then we can work as usual with `getStaticProps`.

AGAIN, `getStaticPaths` is requried to tell next.js which concrete instances of this dynamic page must be pre-generated.

### "getStaticPaths" & Link Prefetching: Behind The Scenes

Pre-rendering of multiple instances of a dynamic page - after `build`.

It pre-renders: for our dynamic page `[id].js` it generates 3 instances `p1 p2 p3`, 3 html pages. Besies that by default it pre-generates the main `index.html` and `404.html` pages.

Besides the pre-generated html files we also have the json files for pre-loading that data if we would navigate to one of this pages directly through a link, not for the initial page load.

Pre-fetching data - in production, if we check the network devtools tab, we see that json files for the dynamic pre-generated page were loaded `p1.json`.. it pre-fetched the props for the dynamic page that would need to be loaded if you click on one of the links that direct to those pages. Again, it pre-fetched this data even before accessing the actual dynamic pages, so on the main page. And now, when we click on a link, we don't send a request to the server and load the pre-rendered html file, instead we stay in this single page app which was loaded and hydrated after the initla request. Instead, JS will render a new page for us just as it would do in a regular app without nextjs, but the data needed for this page is coming from the pre-fetched json file, which it loaded and read under the hood on our behalf, so it doesn't need to fetch the data after we navigated to that page, but so that the data is already there when we do navigate, to show the page faster.

### Fallback Pages

The `fallback` key can help if we have a lot of pages that would need to be pre-generated.

With `fallback: true` We tell next.js that even pages which are not listen in `getStaticPaths`, can be valid, but they are not pre-generated, instead they're pre-generated just in time, when a request reaches the server.

This allows us to pre-generate highlt visited pages by specify the `params` for them, and postpone the generation to less frequented pages to the server, so that they are only pre-generated when they're needed.

BUT, if instead of clicking on a link on our page, but instead directly accessing a url, and sending a new request, then we get an error. Why, because this dynamic pre-generation does not finish instantly.

So, when using this `fallback: true` feature, we should be prepared to return a fallback state in the react component:

```js
function Page(props) {
  const { data } = props;

  if (!data) return <p>Loading</p>;

  return <h1>{data.title}</h1>;
}
```

With this, the page will be rendered, by first rendering the loading paragraph, and then when the data is done loading next.js will give it to the component and the that component will render with that data.

`fallback: 'blocking'` with this we don't need the fallback check in the component, with this next.js will wait for the page to fully be pre-generated on the server before it serves that - this will take a little bit longer for the visitor of the page to get a respone.

## Loading Paths Dynamically

```js
function ProductDetailPage(props) {
  const { loadedProduct } = props;

  return (
    <Fragment>
      <h1>{loadedProduct.title}</h1>
      <p>{loadedProduct.description}</p>
    </Fragment>
  );
}

async function getData() {
  const filePath = path.join(process.cwd(), "data", "dummy-backend.json");
  const jsonData = await fs.readFile(filePath);
  const data = JSON.parse(jsonData);
  return data;
}

export async function getStaticProps(context) {
  const { params } = context;
  const productId = params.pid;

  const data = await getData();
  const product = data.products.find((product) => product.id === productId);

  return {
    props: {
      loadedProduct: product,
    },
  };
}

export async function getStaticPaths() {
  const data = await getData();

  const ids = data.products.map((product) => product.id);
  const pathsWithParams = ids.map((id) => ({ params: { pid: id } }));

  return {
    paths: pathsWithParams,
    fallback: false,
  };
}
```

## Fallback Pages & "Not Found" Pages

Trying to request a page that doesn't exist, but also: `fallback: true` if an ID value is not found, we still want to render a page. Use `notFound`:

```js
export async function getStaticProps(context) {
  const product = undefined;

  if (!product) {
    return { notFound: true };
  }

  return {
    props: {
      loadedProduct: product,
    },
  };
}
```

 -->
