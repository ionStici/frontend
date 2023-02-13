[&larr; Back](./README.md)

# **Create React App**

[Create React App Documentation](https://create-react-app.dev/)

<br>

## **Table of Content**

- [Installation](#installation)
- [predefined commands](#pre-requirements)
- [React App Structure](#react-app-structure)
- [Additional resources](#additional-resources)

<br>

## **Installation**

### **Pre-requirements**

We will use `npm` and `npx` to install and run `create-react-app`

`npm` node package manager (comes with node.js)

`npx` is a package runner tool that comes with `npm`

Upgrade npm to the latest version (in case you are not sure):

```
sudo npm install -g npm@latest
```

### **React Installation**

To initialize react in a project, run the command:

```
npx create-react-app your-project-name --use-npm
```

- `--use-npm` to avoid the default use of _Yarn_ in case you have it installed.

- Use lowecase letters for your project directory name.

<br>

## **Predefined commands**

```JSX
npm start
// Starts the development server

npm run build
// Bundles the app into static files for production

npm test
// Starts the test runner

npm run eject
// Removes this tool and copies build dependencies, configuration files and scripts into the app directory. If you do this, you can't go back.
```

Any changes to the source code will be live-updated.

The source code is compiled to JavaScript at runtime.

<br>

## **React App Structure**

create-react-app created the main structure of the application and some developer settings.

React uses webpack which transforms the directories and files into static assets. With React, we can bypass manual configuration of webpack. [High-level overview of webpack's core concepts](https://webpack.js.org/concepts/)

### **package.json**

- `"private": true` is a failsafe setting to avoid accidentally publishing your app as a public package within the npm ecosystem.
- `dependencies` contains all the required Node modules and versions required for the application. The first three are for testing. `react` and `react-dom` allow us to use react and react-dom in our JavaScript. `react-scripts` provides a useful set of development scripts for working with React.
- `scripts` aliases for the react-scripts commands.
- `browserslist` provides information about browser compatibility of the app.
- `eslintConfig` takes care of the code linting.

### **node_modules**

Contains dependencies and sub-dependencies of packages used by React app, as specified by package.json.

### **package-lock.json**

Contains the exact dependency tree installed in node_modules/. This provides a way for teams working on private apps to ensure that they have the same version of dependencies and sub-dependencies. It also contains a history of changes to package.json, so you can quickly look back at dependency changes.

### **public**

This directory contains assets that will be served directly without additional processing by webpack.

### **src**

This contains the JavaScript that will be processed by webpack and is the heart of the React app.

As your React app grows, it is common to add a components/ directory to organize components and component-related files and a views/ directory to organize React views and view-related files.

<br>

## **Additional resources**

- Documentation: [React Documentation: Getting Started](https://reactjs.org/docs/getting-started.html)
- Tutorial: [Intro to React](https://reactjs.org/tutorial/tutorial.html)
- Article: [Thinking in React](https://reactjs.org/docs/thinking-in-react.html)
- Article: [What the Fork is the React Virtual DOM](https://maggieappleton.com/react-vdom)
- Resource: [Awesome React](https://github.com/enaqx/awesome-react)
- Resource: [Create React App](https://github.com/facebook/create-react-app)
