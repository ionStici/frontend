[&larr; Back](./../README.md)

# React Router

- [React Router Home Page](https://reactrouter.com/en/main)
- External Resource: [What is Routing?](./routing.md)
- Install React Router version 6 `npm install --save react-router-dom@6`

<br>

## Table of Content

- [Providing a Router](#providing-a-router)
- [Linking to Routes](#linking-to-routes)
- [Dynamic Routes](#dynamic-routes)
- [useParams Hook](#useparams-hook)

<br>

## Providing a Router

In the React Router paradigm, the different views of the application (called routes) are just React components. To include them in the application, we just need to render them.

```js
import {
  Route,
  RouterProvider,
  createBrowserRouter,
  createRoutesFromElements,
} from "react-router-dom";
```

```js
const router = createBrowserRouter(
  createRoutesFromElements(
    <Route path="/" element={<Root />}>
      <Route path="about" element={<About />} />
      <Route path="articles" element={<Articles />} />
      <Route path="profile" element={<Profile />} />
    </Route>
  )
);

function App() {
  return <RouterProvider router={router} />;
}
```

`createBrowserRouter` will define a router that prevents URL changes from causing the page to reload. Instead, URL changes will allow the `router` to determine which of its defined routes to render while passing along information about the current URL's path as props.

We make our router available application-wide by providing it using `RouterProvider` the root of our application.

With our `router` in place, we can begin defining the different views, or routes, that our application will render for various URL paths.

React Router gives us two options to define routes: JSX or objects.

The `createBrowserRouter` method accepts an array of `<Route>` objects, so we’ll need to use React Router’s `createRoutesFromElement` method to configure our routes with JSX. We also need to use React Router’s `<Route>` component to define our routes.

The `<Route>` component is designed to render (or not render) a component based on the current URL path. Each `<Route>` component should include:

- A `path` prop indicating the exact URL path that will cause the route to render.
- An `element` prop describing the component to be rendered.

In many cases, there may be certain components, like sidebars, navigation bars, and footers, that we want to render with every page view. We can achieve this by defining a root-level component that contains layout elements we want to render consistently. We can then nest the rest of our routes within this root-level component.

With this route configuration, whenever a user navigates to one of the nested routes, that view will render, along with any elements we’ve defined in our `<Root/>` component.

<br>

## Linking to Routes

```js
import { Link, NavLink } from "react-router-dom";

<Link to="/about">About</Link>
<NavLink to="/about">About</NavLink>
```

`Link` and `NavLink` components work much like anchor tags:

- They have a `to` prop that indicates the location to redirect the user to, similar to the anchor tag's `href` attribute.
- They wrap some HTML to use as the display for the link.

Both links will generate anchor tags displaying the given text and will take the user to the given path indicated within `to` prop when clicked.

The default behavior of an anchor tag - refreshing when the page loads - will be disabled.

If we provide a `/` forward slash, the path will be treated as an absolute path. React Router will assume this path is navigating from the root directory.

The difference between `Link` and `NavLink`: `NavLink`s will automatically have an `'active'` class applied to it. We can also pass a function to `className` or `style` to further customize the styling of an active (or inactive) `NavLink`, like so:

```js
<NavLink
  to="about"
  className={({ isActive }) => (isActive ? "activeNavLink" : "inactiveNavLink")}
>
  About
</NavLink>
```

In the example above we pass a function to the `className` prop which applies the `activeNavLink` class if the `NavLink` is active and `inactiveNavLink` otherwise.

<br>

## Dynamic Routes

**Static Routes** - they match a distinct and unique path.

**Dynamic Routes** - a single route that match any path with the pattern: `/articles/ + title` - and know exactly which component to render.

We can accomplish dynamic routes using React Router URL parameters.

URL parameters are dynamic segments of a URL that act as placeholders for more specific resources.

They appear in a dynamic route as a colon `:` followed by a variable name.

```js
const route = createBrowserRouter(createRoutesFromElement(
    <Route path="articles" element={<Articles />} />
    <Route path="articles/:title" element={<Article />} />
    <Route path="authors/:name" element={<Author />} />
));
```

- the `path` prop `'articles/:title'` contains the URL parameter `:title`.
- This means that when the user navigates to pages such as `'/articles/what-is-react'` or `'/articles/html-and-css'`, the `<Article />` component will render.
- When the `Article` component is rendered in this way, it can access the actual value of that `:title` URL parameter (`what-is-react` or `html-and-css`) to determine which article to display. A single route can even have multiple parameters (eg. `'articles/:title/comments/:commentId'`) or none (eg. `'articles'`).

<br>

## useParams Hook

Use case: Use the value of URL parameters to determine what is displayed in the component that a dynamic route renders.

React Router provides a hook `useParams()` for accessing the value of URL parameters. When called, `useParams()` returns an object that maps the names of URL parameters to their value in the current URL.

```js
import { Link, useParams } from "react-router-dom";

function Article() {
  let { title } = useParams();
  return <h1>{title}</h1>;
}
```

- Inside the `Article` component, `useParams` is called which returns an object.
- We destructure the object to extract the value of the URL parameter from that object, storing it in a variable named `title`.
- We then can use the `title` value for rendering based on some logic.

<br>
