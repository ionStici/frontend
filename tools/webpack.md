# Webpack

## Webpack Project Setup

Install Webpack and Webpack CLI

```
npm install --save-dev webpack webpack-cli
```

- **webpack** package contains the main functionality.
- **webpack-cli** allows command-line access to Webpack.

We want these tools to be developer dependencies because they will not be used when the final product is running. We the `--save-dev` flag to save packages as developer dependencies. **package.json** will list these packages under `devDependencies` for a local project.

p.s. When initiating npm, we can use the `-y` flag to use the default values for the metadata fields: `npm init -y`

## Make an entry point

A Webpack project requires an entry point where it will find the main file to bundle. Webpack will throw a long error indicating a problem with `main` if there are no files at the entry point. The default Webpack entry point is `index.js` in a `src` folder, although this can be changed. If we want to use the default entry point, we should make an `src` folder with an `index.js` inside of it.

```
package.json
src
|--- index.js
```

## Define the Build Command

```json
"scripts": {
    "build": "webpack --watch",
}
```

```
npm run build
```

- The `webpack` command just runs Webpack.
- The `--watch` flag tells Webpack to automatically look for updates to our file and rebuild if any changes occur.
