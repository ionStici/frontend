# Working with File-based Routing

Whatever is in the `public/` folder, for example images, is then served statically. This means that we can reference whatever is in this folder from our code, because the content of `public` is served as part of the overall application.

And because next.js will serve images statically if we place them in the `public/` folder, we can reference them from JSX like: `<img src="/img.jpg" />`, so without the need of importing the image.

Regular React Components should not be in the `pages/` folder. In the `pages/` folder we should have only pages related components, because whatever files we create inside `pages/`, those files will then generate and automatically lead to routes. Instead, create a `components/` folder for react components outside `pages/`.

`pages/project/[id].js` and `pages/project/[...id].js` paths - the route containing only `[id].js` will be rendered when the url will contain only 1 segment such as `example.com/project/bigidea`, but the `[...id].js` file route will render only when the url will contain more than 1 segment, such as `example.com/project/info/guide`, so these 2 routes will not interfere with each other. The three dots path consumes an unlimited amount of segments.

`_app.js` is the root component, where all page components are rendered in.

<br>
