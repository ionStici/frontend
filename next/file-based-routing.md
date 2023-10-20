# File-based Routing

## Introduction

**Next.js** infer routes from the folder structure by rendering react components.

`/pages` directory containing file routes.

`/pages/index.js` special file / main page.

`/pages/about.js` with this, next.js will infer the route: `example.com/about`

Files within `/pages` directory, represent a url route accessible by the name of the file itself.

<br>

## Nested paths & Routes

`/pages/portfolio/index.js` === `example.com/portfolio`

`/pages/portfolio/list.js` === `example.com/portfolio/list`

### Dynamic paths & Routes

`pages/portfolio/[id].js` === `example.com/portfolio/anything`

The square brackets turn the file into a dynamic route, any url string becomes valid by triggering this component whenever the url path does not have an explicit route.

The square brackets `[]` tell next.js that it is a placeholder for any kind of value the url receives which we then have access in the component to dynamically load different kinds of data.

### Extracting Dynamic Path Segment

```js
// next.js hook
import { useRouter } from "next/router";

function Page() {
  const router = useRouter(); // returns an object

  router.pathname; // /portfolio/[id]
  router.query; // {id: 'anything'}

  router.query.id; // anything
  // send a request to the server to fetch data with an id of router.query.id
}
```

### Building Nested Dynamic Routes & Paths

`/pages/clients/[clientid]/[projectid].js` dynamic file within a **dynamic folder**.

`example.com/clients/mike/mike_project` this will render the file above.

The url strings `mike` and `mike_project` are processed dynamically by next.js

```js
router.query; // {clientid: 'mike', projectid: 'mike_project'}
```

<br>

## Catch-All Routes

**three dots** followed by a placeholder name.

Directory structure - `/pages/blog/[...id].js`

URL example - `example.com/blog/2020/10/welcome`

```js
const router = useRouter();
router.query; // { id: ['2020', '10', 'welcome'] }
```

We get an object with a property containing an array with all the url segments.

<br>

## Navigating with the "Link" Component

```js
import Link from "next/link";
```

Navigate to a new route, but prevent the default browser behavior of sending a http request.

```js
<Link href="./about">About</Link>
```

_Additional `Link` prop examples:_

- The `replace` prop will prevent pushing the new route, but instead it will replace the current page with that new route, this will don't store the routes in the browser history api.

### A Different Way Of Setting Link Hrefs

```js
<Link href={{ pathname: "/clients/[id]", query: { id: "mike" } }}>Mike</Link>
```

_The `href` prop receives an object with the following properties:_

- `pathname` for the actual path
- `query` for the path placeholder

<br>

## Navigating Programmatically

_Imperative Navigation_

```js
const router = useRouter();

function navigate() {
  router.push("/clients/mike/a");

  router.push({
    pathname: "/clients/[client][project]",
    query: { client: "mike", project: "a" },
  });
}
```

`router.push()` method to programmatically navigate to a different page.

Just like `Link` with `href`s, `push()` accepts an object with routes.

`router.replace()` to replace the current page instead of pushing (we can't go back after navigation).

<br>

## Adding a Custom 404 Page

`/pages/404.js`

Next.js will always load the component returned by `404.js` file when a 404 error arises.

<br>

## Review

**File-based Routing (NextJS):**

- No extra boilerplace code required
- Intuitive system
- File + folder structure influences routes
- Navigation works with `<Link>` component and imperatively

**Code-based Routing (React + react-router):**

- Boilerplace setup in code requried
- Straightforward but includes new components + concepts
- File + folder setup does not matter at all
- Navigation works with `<Link>` component and imperatively

**Conclusion:** NextJS file-based routing is more intuitive and easier to set up

<br>

# Working with File-based Routing

Whatever is in the `public/` folder, for example images, is then served statically. This means that we can reference whatever is in this folder from our code, because the content of `public` is served as part of the overall application.

And because next.js will serve images statically if we place them in the `public/` folder, we can reference them from JSX like: `<img src="/img.jpg" />`, so without the need of importing the image.

Regular React Components should not be in the `pages/` folder. In the `pages/` folder we should have only pages related components, because whatever files we create inside `pages/`, those files will then generate and automatically lead to routes. Instead, create a `components/` folder for react components outside `pages/`.

`pages/project/[id].js` and `pages/project/[...id].js` paths - the route containing only `[id].js` will be rendered when the url will contain only 1 segment such as `example.com/project/bigidea`, but the `[...id].js` file route will render only when the url will contain more than 1 segment, such as `example.com/project/info/guide`, so these 2 routes will not interfere with each other. The three dots path consumes an unlimited amount of segments.

`_app.js` is the root component, where all page components are rendered in.

<br>
