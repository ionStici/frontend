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
