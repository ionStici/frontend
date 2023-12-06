# Draft

## Component Categories

- Stateless / Presentational Components

  No state

  Receive props

  Simply present data

- Stateful Components

  Have state

- Structural Components

  Pages, layouts of the app, Provides structure

  Result of composition of components

**Prop Drilling** occurs when a parent component passes data down to its children and then those children pass the same data down to their own children.

**Component Composition** - technique of combining different components using the `children` prop (or explicitly defined props) / for reusable and flexible components / to fix a prop drilling problem / great for creating layouts

## Explicit Prop

Passing Components as Props (Alternative to children)

```jsx
function App() {
  return <Layout element={<Component />} />;
}

function Layout({ element }) {
  return <main>{element}</main>;
}
```
