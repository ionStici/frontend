[&larr; Back](./README.md)

# Create React App

[Create React App Documentation](https://create-react-app.dev/)

## Installation

```
npx create-react-app your-project-name --use-npm
```

- `--use-npm` to avoid the default use of _Yarn_ in case you have it installed.
- Use lowecase letters for your project directory name.

<br>

## Predefined commands

- `npm start` - Starts the development server
- `npm run build` - Bundles the app into static files for production
- `npm test` - Starts the test runner
- `npm run eject` - Removes this tool and copies build dependencies, configuration files and scripts into the app directory. If you do this, you can't go back.

<br>

## React App Structure

`create-react-app` created the main structure of the application and some developer settings.

React uses webpack to transform directories and files into static assets.

- **public**

  This directory contains assets that will be served directly without additional processing by webpack.

- **src**

  This contains the JavaScript that will be processed by webpack and is the heart of the React app.

- **package.json**

  `"private": true` is a failsafe setting to avoid accidentally publishing your app as a public package within the npm ecosystem.

  `dependencies` contains all the Node modules and versions required for the application. The first three are for testing. `react` and `react-dom` allow us to use react and react-dom in our JavaScript. `react-scripts` provides a useful set of development scripts for working with React.

  `scripts` tasks / commands.

  `browserslist` provides information about browser compatibility of the app.

  `eslintConfig` takes care of the code linting.

- **node_modules**

  Contains dependencies and sub-dependencies of packages used by React app, as specified by package.json.

- **package-lock.json**

  Contains the exact dependency tree installed in node_modules/. This provides a way for teams working on private apps to ensure that they have the same version of dependencies and sub-dependencies. It also contains a history of changes to package.json, so you can quickly look back at dependency changes.
