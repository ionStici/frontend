# Page Pre-Rendering & Data Fetching

## Table of Content

- [Introduction](#introduction)
- [Static Site Generation with "getStaticProps"](#static-site-generation-with-getstaticprops)
- ["getStaticProps"](#getstaticprops)

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
