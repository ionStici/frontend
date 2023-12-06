[&larr; back](./README.md)

# Theming

## Customize the browser interface

The browser's interface adapts to your suggested color.

```html
<meta name="theme-color" content="#00D494" />
```

- You can change this setting using JavaScript.

Also, you can specify a theme color in a [web app manifest file](https://developer.mozilla.org/en-US/docs/Web/Manifest) linked to your HTML document. Read: [Add a web app manifest](https://web.dev/add-manifest/).

<br>

## prefers-color-scheme

`prefers-color-scheme` media feature - detect OS's theme setting (light or dark).

```css
@media (prefers-color-scheme: dark) { dark theme styles }
@media (prefers-color-scheme: light) { light theme styles }
```

Example for `theme-color` meta tag:

```html
<meta name="theme-color" content="#" media="(prefers-color-scheme: dark)" />
```

<br>

## Theming with custom properties

Use CSS custom properties for theme styling, and then update them within a `prefers-color-scheme` media query.

```css
html {
  --page-color: white;
}

@media (prefers-color-scheme: dark) {
  html {
    --page-color: black;
  }
}
```

[Building a color scheme](https://web.dev/building-a-color-scheme/) for more advanced examples of themeing with custom properties.

<br>

## prefers-color-scheme in the picture element

```html
<picture>
  <source srcset="darkimage.png" media="(prefers-color-scheme: dark)" />
  <img src="lightimage.png" alt="A description of the image." />
</picture>
```

<br>

## Default Form Styles

Let the browser know your site's theme mode, so that it could provide the appropriate default styling for forms and other elements.

```css
html {
  color-scheme: light;
}
@media (prefers-color-scheme: dark) {
  html {
    color-scheme: dark;
  }
}
```

```html
<meta name="supported-color-schemes" content="light dark" />
```

<br>
