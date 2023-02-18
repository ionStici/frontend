[&larr; Back](./README.md)

# Separate Container Components From Presentational Components

_Separating container components from presentational components_ is a popular React programming pattern.

If a component has to have state, make calculations based on props, or manage any other complex logic, then that component shouldn’t also have to render HTML-like JSX.

The functional part of a component (state, calculations, etc.) can be separated into a container component.

## Separate Presentational Component

**Presentational Component:** its only job is to contain JSX.

It will not render itself because a presentational component will always get rendered by a container component.

Example: we have `Presentational` and `Container` components. `Presentational.js` must export its component, and `Container.js` must import that component.

```js
// Directory Structure

components/  // folder for presentational components
---| Presentational.js  // component that only contains JSX, but not render anything

containers/  // folder for handling logic
---| Container.js  // will render the Presentational.js

```

## Render Presentational Component in Container Component

- Container component for logic.
- Presentational component contains and render JSX.

The container component should render the presentational component instead of rendering its own JSX.

The presentational component should be left with the render function that contains JSX statements. This component’s only job is to render HTML-like JSX. Delete everything inside of the presentational component class, except for the render function. When you’re done, the class should only have one method: render()

```jsx
class CompContainer extends React.Component {
  // contains logic

  render() {
    return <CompPresentational />;
  }
}

root.render(<CompContainer />);
```

<br>

_Resources_

- [Container Components](https://medium.com/@learnreact/container-components-c0e67432e005)
- [Presentational and Container Components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)
