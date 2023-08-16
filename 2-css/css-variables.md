[&larr; back](./README.md)

# Custom Properties

CSS Custom Properties (CSS Variables)

```scss
:root {
  --color-1: #ccc; // Declare
}

.text {
  color: var(--color-1, white); // Use
}
```

- A custom property must be prefixed with two dashes `--` and are case sensitive.
- The `var()` function takes the custom property and returns its declared value.
- We can pass a fallback as second argument in case the custom property fails.
- It must be defined in a declaration block, and it is scoped to that block.
- To make CSS variables available everywhere, declare them inside `:root`

<br>

## Edit CSS Variables in JavaScript:

```js
const root = document.documentElement;
root.style.setProperty("--color-1", "#ddd");
```

<br>
