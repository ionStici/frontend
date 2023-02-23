[&larr; Back](./README.md)

# Styled Components

[Styled Components](https://styled-components.com/)

<br>

<!-- [&larr; Back](./README.md)

# Emotion

## Table of Content

- [Instalation](#instalation)
- [The css Prop](#the-css-prop)
  - [Object Styles](#object-styles)
  - [String Styles](#string-styles)
- [Styled Components](#styled-components)
- [Composition](#composition)
- [Theming](#theming)
- [Keyframes / Animation](#keyframes--animation)

<br>

## Instalation

Install the [Emotion](https://emotion.sh/docs/introduction) library for a React app

```
npm i @emotion/react
```

Import the CSS prop from emotion

```js
/** @jsxImportSource @emotion/react */
import { css } from "@emotion/react";
```

This comment informs Babel to customize the automatic runtime import.

<br>

## The css Prop

[The css Prop](https://emotion.sh/docs/css-prop)

```jsx
const Comp = function () {
  return (
    <div>
      <h2
        css={{
          fontFamily: "monospace",
          fontSize: "24px",
        }}
      >
        Hello
      </h2>
      <p
        css={css`
          font-size: 16px;
          color: #333;
        `}
      >
        lorem text
      </p>
    </div>
  );
};
```

### Object Styles

The `<h2>` element uses an object for styling: [Object Styles](https://emotion.sh/docs/object-styles).

Particularities: camelCase, properties separated by a comma. Object styles can also be used with styled components.

### String Styles

The `<p>` element uses tagged templated literals.

Particularities: kebab-case, separated by a semicolon.

<br>

## Styled Components

[Emotion library package](https://emotion.sh/docs/styled): `@emotion/styled`.

It gives as access to `styled` that allows you to create components that have styles attached to them.

It is called with an HTML tag or React component.

Install `styled` package from the Emotion library:

```
npm i @emotion/styled
```

Import `styled`:

```
import styled from "@emotion/styled";
```

Styled Component:

```jsx
export const SecondHeading = styled.h2`
  font-size: 20px;
  color: red;
`;
```

1. On the `styled` object we attach a HTML element name and then a template literal with css styles.
2. We store the HTML element and its styles in a variable.
3. We use and render that variable as a component.

Use the styled component:

```jsx
function Comp() {
  return <SecondHeading>Hello World</SecondHeading>;
}
```

<br>

## Composition

We can use [composition](https://emotion.sh/docs/composition) to create variants.

For styling a variant, we attach to the `styled` object the original component name, wrapped in parentheses, and then we define the new CSS styles.

```js
import styled from "@emotion/styled";

export const Button = styled.button`
  font-size: 16px;
`;

export const PrimaryButton = styled(Button)`
  background-color: #03045e;
  color: #caf0f8;
`;

export const SecondaryButton = styled(Button)`
  background-color: #caf0f8;
  color: #03045e;
`;
```

Importing:

```js
import { PrimaryButton, SecondaryButton } from "./styles.js";

function Comp() {
  return (
    <div>
      <PrimaryButton>Button 1</PrimaryButton>
      <SecondaryButton>Button 2</SecondaryButton>
    </div>
  );
}
```

Notice that we import only the variants.

<br>

## [Theming](https://emotion.sh/docs/theming)

```js
import styled from "@emotion/styled";

export const theme = {
  colors: {
    primary: "#03045e",
    secondary: "#caf0f8",
    tertiary: "#023e8a",
    quaternary: "#fff",
  },

  fonts: {
    primary: "helvetica",
  },

  fontSize: {
    primary: "20px",
    secondary: "14px",
  },
};

export const SecondHeading = styled.h2`
  font-size: 20px;
  color: ${theme.colors.primary};
`;
```

Importing:

```jsx
import { css, ThemeProvider } from "@emotion/react";
import { theme, SecondHeading } from "./style.js";

function Comp() {
  return (
    <ThemeProvider theme={theme}>
      <SecondHeading
        css={(theme) => ({
          color: theme.colors.primary,
        })}
      >
        Hello World
      </SecondHeading>
    </ThemeProvider>
  );
}
```

Import `ThemeProvider` from emotion library.

Wrap the entire content in a `<ThemeProvider>` component: Add the `<ThemeProvider>` at the top level of the application which accesses the theme object. This will make the theme property available to all components in the React app.

We can also update the `theme` object from our tags.

<br>

## Keyframes / Animation

We can define animations using the [`keyframes`](https://emotion.sh/docs/keyframes) helper from `@emotion/react`.

`keyframes` takes in a CSS keyframe definition and returns an object you can use in styles. You can use strings or objects just like css.

```js
import { keyframes } from "@emotion/react";

export const LogoSpin = keyframes`
from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
`;
```

Importing:

```js
import { LogoSpin } from "./styles";

// ...
<img
  src={logo}
  alt=""
  css={css`
    animation: ${LogoSpin} 10s linear infinite;
  `}
/>;
// ...
```

<br> -->
