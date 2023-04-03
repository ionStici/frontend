[&larr; Back](./README.md)

# Styling Links

Styling Anchor Elements

Links are for navigating on the page, while button elements should be used for actions.

<br>

## Anchor Element

More about [The Anchor element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)

```css
a,
a:link,
a:visited {
  color: #466995;
  text-decoration: underline;
  cursor: pointer;
}

a:hover {
  color: orange;
  text-decoration: none;
}

a:active {
  color: blue;
}
```

When styling links, take in account: Usability, Accessibility, SEO.

Link states: `link`, `visited`, `hover`, `active`.

Always use `link` and `visited` states for anchor elements.

<br>
