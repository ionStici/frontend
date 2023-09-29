[&larr; Back](./README.md)

# JavaScript Build Process: Overview

Let's say that we are done writing our project code (it contains multiple modules), so **the development step is complete**. Now, our project needs to go through a **build process**, where one big final bundle is built, ready to be deployed on the web server for production. **Production** means that the application is being used by real users in the real world.

What does a **Build Process** do? Bundle all JS modules into one script, eliminate unused code, compress code. Why only 1 script? Better for performance, older browsers don't support native modules.

**Transpiling and Polyfilling** - convert modern JS features to ES5 syntaxes (supportability reasons / build process done by Babel tool).

To implement a build process we use Module Bundler tools like: Webpack, Parcel, Vite.

- **Parcel** - fast module bundler, easy to use, works without any configuration.
- **Webpack** - popular and complex module bundler.

<br>
