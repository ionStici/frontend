# Optimizing NextJS Apps

## Configuring the "head" Content

Add `<head>` metadata using `Head` next.js component.

We can add this `Head` special component anywhere in our JSX code for a given component.

Next.js will inject the content of the `Head` component into the `<head>` section of the page.

```js
import Head from "next/jead";

function HomePage() {
  return (
    <div>
      <Head>
        <meta name="description" content={event.description} />
        <title>Hello World!</title>
      </Head>
      <main></main>
    </div>
  );
}
```

We can inject dynamic content inside `Head` as usual.

## Reusing Logic Inside A Component

In case a component has multiple checks using the `return` statement..

```jsx
function HomePage() {
  const pageHeadData = (
    <Head>
      <title>Hello World!</title>
    </Head>
  );

  if (!firstCheck) {
    return (
      <>
        {pageHeadData}
        <div></div>
      </>
    );
  }

  if (true) {
    return (
      <>
        {pageHeadData}
        <div>content</div>
      </>
    );
  }
}
```

Standard React way of re-using logic.

## Working with the `"_app.js"` File (and Why)

Head settings that are the same across all page components.

`_app.js` is the root app component, which in the end is rendered for every page that is deing displayed.

This component `<Component {...pageProps} />` which is received through `props` in `MyApp` component, is the actual page component that should be rendered.

Again, the `MyApp` component is automatically rendered by Next.js, then the `Component` prop is automatically set by Next.js, so you don't need to do anything for that.

We can use this `_app.js` file such that we wrap the page component is a wrapper component, to give all pages the same layout, for example the same navigation bar.

```js
// _app.js

function MyApp({ Component, pageProps }) {
  return (
    <>
      <Head>
        <meta name="viewport" content="initial-scale=1.0, width-device-width" />
      </Head>
      <Component {...pageProps} />
    </>
  );
}
```

As well, we can use `Head` component here to apply some generic setting that applies to all our page components.

## Merging "head" Content

Next.js automatically merges multiple `Head` elements.

If we have conflicts, then next.js will simply take the latest `Head` setting in case we have it multiple times.

If we have a general `<title>` in the `_app.js` file, it will be overwritten in situations where we navigate to page components that have their own `<title>` set.

## The `_document.js` File
