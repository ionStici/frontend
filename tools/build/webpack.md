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

<br>

## Make an entry point

A Webpack project requires an entry point where it will find the main file to bundle. Webpack will throw a long error indicating a problem with `main` if there are no files at the entry point. The default Webpack entry point is `index.js` in a `src` folder, although this can be changed. If we want to use the default entry point, we should make an `src` folder with an `index.js` inside of it.

```
package.json
src
|--- index.js
```

<br>

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

<br>

## Creating a Webpack Config

Webpack automatically looks for a configuration file named `webpack.config.js`. We define Webpack's settings in an object defined using the [`module.exports`](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export) syntax.

```js
module.exports = {
  mode: "development",
};
```

- `development` mode is used when we develop our app, producing a more readable version of the output.
- We switch to `production` when we have a finished version, which makes the output less readable and more compact.

[Webpack Modes](https://webpack.js.org/configuration/mode/)

<br>

## Defining Entry and Exit Points

Webpack default entry point: `./src/index.js`

Manually define the entry point:

```js
const path = require("path");

module.exports = {
  entry: "./app/home.js",
  output: {
    filename: "script.js",
    path: path.resolve(__dirname, "build"),
  },
};
```

We can define an exit point under the `output` configuration option. Here we can define the name of the final js bundle, and also the directory name.

Given the configuration above, running webpack would produce: `build/script.js`

- Entry point: a path relative to where the `webpack.config.js` is located.
- Exit point: a relative path.

The `path.resolve()` method combines the path to the current directory with the folder name we want to place the bundled code in.

<br>

## Viewing Our App with Webpack Dev Server

Install `webpack-dev-server` as a development dependency in a local environment:

```
npm install --save-dev webpack-dev-server
```

Next, we need an HTML document, and it should embed the JavaScript from our exit point:

```html
<script src="./dist/main.js"></script>
```

To use `webpack-dev-server`, we’ll add `start` command to `package.json` inside of the `scripts` section:

```js
"build": "webpack --watch",
"start": "webpack serve"
```

This is building our project and then serving it to the browser.

The `build` command is going to compile our project as well as update it when we make changes.

The `serve` command is going to serve our build and refresh when the build changes.

In order to have our project update any time we make changes, we would typically run each of these commands in a separate terminal.

We would first run the `build` command in one terminal, to create the bundle and wait for updates.

```
npm run build
```

We would next launch a second terminal and run the start command to serve the site.

```
npm run start
```

<br>

## Introduction to Webpack Rules

Webpack uses _rules_ to know what to do with different file types.

Webpack expects an array of `rules` in a configuration option called `module`.

```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.txt$/i,
        type: "asset/source",
      },
      {
        test: "",
        type: "",
      },
    ],
  },
};
```

A rule has a `test` configuration option defined as a regular expression.

If a file matches the regular expression, webpack will use the rule of that file.

The other part of the rule needs to tell Webpack what to do with files that match the `test`. That part of the rule varies by file type.

`type: 'asset/source` is telling webpack that `.txt` files are an asset that can be added directly to the source code, not requiring much processing.

Once we add a rule for a file type, we can import files of that type into our code. Example:

```js
import Text from "./example.txt";
document.querySelector("h1").innerHTML = Text;
```

Previewing this code replaces the content of the page `h1` element with the file content.

<br>

## Adding CSS to Our Builds

configuration option for CSS: `test: /\.css$/i`

White we import `.txt` files as assets, other file types often need _loaders_ to get bundled by Webpack.

Instead of a `type` attribute, files that use one or several loaders require a `use` attribute.

CSS files use two loaders, `css-loader` and `style-loader`. `css-loader` takes the CSS out of a `.css` file and adds it to the JavaScript code. `style-loader` takes the output of `css-loader` and puts it in a `style` tag in the HTML. We need both loaders and to apply `css-loader` first. We specify multiple loaders with an array, and Webpack applies them in reverse order.

Rule for CSS files:

```js
{
    test: /\.css$/i,
    use: ['style-loader','css-loader']
}
```

In a local environment, we’d also install the loaders as developer dependencies.

```js
npm install --save-dev style-loader css-loader
```

We can then import CSS files directly into out JavaScript:

```js
import "./style.css";
```

When we build and start our preview server, the CSS is applied to the HTML!

<br>

## Adding Images to Our Builds

Since Webpack 5, images and fonts no longer need a loader, and can use Webpack’s `asset` system. Their rules are similar to that of .txt files.

`asset/resource` creates a file in the build and imports it into the code as a URL. [Asset Types](https://webpack.js.org/guides/asset-modules/).

```js
{
  test: /\.(png|svg|jpg|jpeg|gif)$/i,
  type: 'asset/resource'
}
```

Using the syntax above we can handle many image types.

When an image rule has been defined in `webpack.config.js`, we can import images into our JavaScript as if they were code:

```js
import Square from "../square.png";
```

<br>

## Adding Fonts to Our Builds

The font rule is similar to the image rule:

```js
{
  test: /\.(woff|woff2|eot|ttf|otf)$/i,
  type: 'asset/resource'
}
```

The above rule would support .woff, .woff2, .eot, .ttf, and .otf font files.

Unlike the other resources we’ve seen so far, font files are imported in CSS, not in JavaScript. We use a font in our CSS like so:

```css
@font-face {
  font-family: "Roboto-Black";
  src: url("../Roboto-Black.ttf");
}

h1 {
  font-family: "Roboto-Black";
}
```

## Steps

### Part 1 - Configuring the Node Project

```
npm init -y
```

```json
// package.json
"scripts": {
    "build": "webpack --watch",
    "start": "webpack serve --open"
}
```

```
npm install --save-dev webpack webpack-cli webpack-dev-server style-loader css-loader
```

### Part 2 - Configuring Webpack

`webpack.config.js`

```js
module.exports = {
  mode: "development",
  entry: "./src/index.js",
  rules: [
    {
      test: /\.css$/i,
      use: ["style-loader", "css-loader"],
    },
    {
      test: /\.(png|svg|jpg|jpeg|gif)$/i,
      type: "asset/resource",
    },
    {
      test: /\.(woff|woff2|eot|ttf|otf)$/i,
      type: "asset/resource",
    },
  ],
};
```

### Part 3 - Bundling the CSS

Delete the ref link in the `head` tag of the HTML, and import the CSS within `index.js`

### Part 4 - Bundling the JavaScript

With Webpack, we need only one `script` tag in out HTML.

Add a `script` tag that embeds the JS code that will be at the exit point.

```js
<script src="dist/main.js"></script>
```

We link our JavaScript content using `import` and `export` statements.

### Part 5 - Bundling Images

```js
import img from "./asset/img.png";
```

### Part 6 - Building and Viewing Our App

Two terminal windows in the project directory:

Run the `build` command on one terminal window, and the `start` command in the other.

<br>
