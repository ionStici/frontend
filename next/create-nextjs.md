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

## Analyzing The Created Project

`pages` most important, file based routing, define the different pages that will make up the app.

`public` public resources

`styles` for css

In our NextJS app we don't have a html document as we would do in a react app, that's because NextJS has built-in pre-rendering, it gives you that single-page-application dynamically pre-rendered when the request reaches the server.

NextJS allows us to determine WHEN a page should be pre-rendered.

Execute: `npm run dev`

What we see on the page after live hosting, is the result of the `index.js` file from `pages` directory. This file contains a regular react component, but this component is actually now pre-rendered. In DevTools, we can see that all the html markup is in place, not just the `div` element with the `app` id.

NextJS key feature: Build in page pre-rendering.

<br>

<br>
