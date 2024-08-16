# Installing and Configuring TypeScript

## Table of Contents

- [Installing TypeScript Globally](#installing-typescript-globally)
- [Installing TypeScript Locally via npm](#installing-typescript-locally-via-npm)
- [Generating a `tsconfig.json` File](#generating-a-tsconfigjson-file)
- [Common TypeScript Configurations](#common-typescript-configurations)

## Installing TypeScript Globally

To install TypeScript globally on your system, use the following command:

```bash
npm install --global typescript
```

- After installing TypeScript globally, you can use the `tsc` (TypeScript compiler) command from any directory.

```bash
tsc index.ts
```

The `tsc` command will transpile `index.ts` TypeScript file into a new JavaScript file named `index.js`.

## Installing TypeScript Locally via npm

To add TypeScript as a local development dependency in your project, use:

```bash
npm install typescript --save-dev
```

- Once installed, you can use the `tsc` command from your terminal to transpile TypeScript files.
- To continuously watch for changes and transpile TypeScript automatically, use the `--watch` flag.
- Add a script to your `package.json` for convenience:

```json
"scripts": {
  "tsc": "tsc index.ts --watch"
}
```

Then, run the script using:

```bash
npm run tsc
```

This will keep `tsc` running in watch mode, automatically recompiling your TypeScript files as you make changes.

## Generating a `tsconfig.json` File

To create a `tsconfig.json` file in your project, run:

```bash
tsc --init
```

The `tsconfig.json` file contains the configuration options for the TypeScript compiler. It allows you to customize the behavior of the TypeScript compiler, such as specifying which files to include, target ECMAScript version, module resolution strategies, and much more.

## Common TypeScript Configurations

### Using Community-Created Configurations

To speed up setup, you can use a community-maintained configuration base. For example, to install a recommended configuration base:

```bash
npm install --save-dev @tsconfig/recommended
```

Then, extend this base in your `tsconfig.json`:

```json
{
  "extends": "@tsconfig/recommended/tsconfig.json",
  "compilerOptions": { ... }
}
```

You can override specific options as needed.

### Creating a Shared Configuration

You can create a custom base configuration to reuse across multiple projects. Define your options in a JSON file:

```json
// custom-tsconfig.json
{
  "compilerOptions": {
    "target": "esnext",
    "strict": true,
    "noUnusedParameters": true,
    "noUnusedLocals": true
  }
}
```

Then, extend this custom configuration in your `tsconfig.json`:

```json
{
  "extends": "./custom-tsconfig.json",
  "compilerOptions": { ... }
}
```
