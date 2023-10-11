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

## "getStaticProps" & Configuration Options

`getStaticProps` function when called (by next.js) receives an argument.

```js
export async function getStaticProps(context) {}
```

`context` - object with extra information about the page when the function is executed, for example: dynamic params, dynamic path segment values.

### Third key: notFound

```js
export async function getStaticProps() {
  //

  return {
    props: {},
    revalidate: 10, //
    notFound: false,
  };
}
```

`notFound` wants a boolean value, if `true` then the page will return a `404` error and therefore will render the `404.html` page, in can use this in our advantage in case the code we fetched in the function body returned an error and then we dynamically return 404.

### redirect key

redirect the user to another page, use case: based on data fetching.

```js
if (!data) {
  return {
    redirect: {
      destination: "/no-data",
    },
  };
}

return {
  props: {},
};
```

If no `data`, then redirect the page to `no-data` route instead of this current page.

<br>

## Working with Dynamic Parameters

Extracting `params` in the component function using `useRouter`, we work with params in the browser.

For pre-rendering a page, where we prepare the data for pre-rendering the page, then this happens on the server, for example using `getStaticProps` which runs before the component function runs.

We can use the `context` object that `getStaticProps` receives to work and get access to `params` (to the dynamic path segment) inside this pre-generating function, so that we could prepare the data for the component before it runs. Then we don't need to extract that dynamic segment in the component function.

### "getStaticPaths" For Dynamic Pages

If we have a dynamic page with square brackets `[id].js` then the default behavior is not to pre-generate the page with `getStaticProps`, because technically we will have multiple pages with different data, next.js doesn't know in advance how many pages to generate. Instead, these pages are always generated just in time on the server. Now it doesn't work because we added `getStaticProps`.

When we add `getStaticProps()` function to a page component file, then we tell next.js that you want to pre-render the page in advance.

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

<br>

## "getServerSideProps" for Server-side Rendering (SSR)

Static Generation AND **Server-side Rendering**.

Inside getStaticProps and getStaticPaths we don't have access to the actual incoming request - instead, these are generally called when the project is `build`, except with incremental static generation.

Server-side rendering means that you do need to pre-render a page for every incoming request. So not at most every second, but really for every incoming request, and/or you need access to the concrete request object that is reaching the server, because for example you need to extract cookies.

Next.js supports: run "real server-side code" - next.js gives you a function which is executed whenever a request for this page reaches the server. So that's then no pre-generated in advance during build time or every couple of seconds but it's really code that runs on the server only, only after you deployed it, and which is then re-executed for every incoming request. This function needs to be exported and needs to be added to a page component file.

```js
export async function getServerSideProps() {}
```

NextJS will execute this function whenever a request for this page is made.

Therefore, you should ONLY use either `getStaticProps()` or `getServerSideProps`, because they kind of clash. They fulfill the same purpose, they get props for the component so that nextjs is then able to render that component, but they run at different points of time .

### getServerSideProps

```js
export async function getServerSideProps(context) {
  return {
    props: {
      username: "Max",
    },
    notFound: false,
    redirect: false,
  };
}
```

It accepts the same keys as `getStaticProps` except the `revalidate` key, because `getServerSideProps` per definition runs for every incoming request, so there's no need to revalidate after a certain amount of seconds because it will always run again.

The props of `getServerSideProps` will then be made available to the component function, but it will not be called in advanced whenw e `build` the project, but really for every incoming request.

Important: this `getServerSideProps` only executes on the server after deployment (also on our development server), but it's not statically pre-generated.

### context

The `context` object of `getServerSideProps` function - here we get access to request and response objects, and still to the `params` as well.

```js
export async function getServerSideProps(context) {
  const { params, req, res } = context;
}
```

These are default nodejs objects for incoming [messages](https://nodejs.org/api/http.html#http_class_http_serverresponse) and for [responses](https://nodejs.org/api/http.html#http_class_http_incomingmessage).

Getting access to this kind of data can be useful for example when we need a special header or cookie data.

`getServerSideProps()` is good if we want to ensure that this function runs for every incoming request, so that it's never statically pre-generated, for situations when we have highly dynamic data that can get outdated fast. And we can still write server-side code here or reach out to json files from the project directory, and it still returns props for the component function, the only key difference is the kind of data we get access to in the `context` object and the timing of this function.

### Dynamic Pages & "getServerSideProps"

When we use dynamic routes with `getStaticProps`, we need `getStaticPaths` to tell nextjs explicitly the routes. With `getServerSideProps` everything works well without `getStaticPaths`, why? Because `getServerSideProps` runs on the server anyways, so nextjs does not pre-generate any pages at all anyway.

```js
// [uid].js

function UserIdPage(props) {
  return <h1>{props.id}</h1>;
}

export default UserIdPage;

export async function getServerSideProps(context) {
  const { params } = context;

  const userId = params.uid;

  return {
    props: {
      id: "userid-" + userId,
    },
  };
}
```

### "getServerSideProps": Behind The Scenes

Note that details about the build we get in the terminal where we run the script.

Pages that use `getServerSideProps` are not pre-generated, fact denoted by the **lambda** λ symbol, instead will be pre-rendered on the server only.

Why we use these function - `getStaticProps getStaticPaths getServerSideProps` - Prepare data for our components ahread of time OR on the server so that we ca serve a finished page to the client, that can offer a better user experience to our users, since they get the finished page and all the content is there right from the start, but it also help us with search engines, with SEO, because search engines also see the finished page.

<br>

## Implementing Client-Side Data Fetching

**Client-Side Data Fetching with Next.js**

**Firebase** is a service offered by Google which gives you an entire backend with a lot of features, one of te features is a database with an attached API.

We will use `realtime` database.

_Standard react way ot sending a request:_

```js
import { useEffect, useState } from "react";

function LastSalesPage() {
  const [sales, setSales] = useState();
  const [isLoading, setIsLoading] = useState(false);

  useEffect(() => {
    setIsLoading(true);

    fetch("https://nextjs-tst-default-rtdb.firebaseio.com/sales.json")
      .then((res) => res.json())
      .then((data) => {
        const transformedSales = [];

        for (const key in data) {
          transformedSales.push({
            id: key,
            username: data[key].username,
            volume: data[key].volume,
          });
        }

        setSales(transformedSales);
        setIsLoading(false);
      });
  }, []);

  if (isLoading) {
    return <p>Loading...</p>;
  }

  if (!sales) {
    return <p>No data yet</p>;
  }

  return (
    <ul>
      {sales.map((sale) => (
        <li key={sale.id}>
          {sale.username} - ${sale.volume}
        </li>
      ))}
    </ul>
  );
}

export default LastSalesPage;
```

If we inspect the source we see the paragraph `No data yet`, why? when next.js pre-renders the page, it will not execute `useEffect`, it will just return and pre-render the very basic first version of waht the component returns, and that is the paragraph `No data yet`.

SO, we still have pre-rendering BUT without the data, because we're fetching the data on the client side now, with the above approach.

## useSWR

The above pattern is such a common pattern that we can use a custom hook for this job, `SWR` hook.

https://swr.vercel.app/

This is a react hook developed by the next.js team, but we can use it in non-next.js projects as well.

This is a hook that under the hood, still will send a http request, by default using the fetch api,

<hr/>

Note: You must now add a default "fetcher" when working with `useSWR`:

```js
useSWR(<request-url>, (url) => fetch(url).then(res => res.json()))
```

<br>
