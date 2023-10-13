# API Routes

## What are API Routes?

- API - Application Programming Interface

- REST API = Representational State Transfer (a specific structure of web APIs)

API: We have a web server that exposes certain URLs (APIs) that can accept data and then send back a response (json is the most common format of data exchange).

API routes - special kind of URLs which we can add to a next.js app - which are about getting data, using data, maybe storing data in some database, and sending back data in any form of your choice.

API routes (next.js feature) is a feature that allows us to build a REST API as part of our next.js app. It also allows us to support URLs / paths after our domain, then also accepting different kind of request methods, then depending on which http method was used for which path, different actions could be triggered. For example, for a POST request we might expect some data to be sent along with that incoming request, then when that request hits the API, we extract that data from the request and store it in a database. If a GET request reaches the URL, we might want tof etch data from a database (as raw data in JSON format).

These requests are sent and triggered by JavaScript code (Ajax).

## Writing a API Route

API Routes (next.js feature).

Add API endpoints to next.js app directory: `pages/api`

`api` - special folder (it has to be called like this) that is recognized by next.js, any file within this `api` folder will be treated in a special way.

In this `api` folder, we can add pages just as we can add them anywhere else in the `pages` folder.

`pages/api/feedback.js` - this will create a path we can send requests to.

Inside of any file from the `api` folder, we don't export a react component, instead we create and export a `handler` function that will receive 2 parameters: a request object `req` and a response object `res`.

In this `handler` function we can execute server-side code - any code we write here will not end up in any client-side bundle, code from here will not be exposed to visitors of our webpage, just as code from `getStaticProps` and `getServerSideProps`.

This function is executed by next.js for incoming requests sent to `/api/feedback`. In can write node.js code here.

We can send back a resonse with help of the `res` object that contains special methods for sending back response and to configure that response.

```js
export default function handler(req, res) {
  res.status(200).json({ message: "This works!" });
}
```

This line of code from the `handler` function from `/pages/api/feedback.js` will be executed by next.js when we send a request to `/api/feedback`, and this code will then send back a response.

If we make a request to `/api/feedback` by directly accessing the url in the browser, then we get on the page: `{"message":"This World!"}` - but this is not how we do this requests - we can check more about this in the network tab of devtools, for example the reponse itself. In Headers tab of network, the Content-Type is set to application/json. So this is a special kind of page, files from `pages/api/file.js` allows us to run our own server side code, and to add our own app focused API, we can add features like newsletter, user feedback submission, etc.
