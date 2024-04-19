[&larr; Back](./README.md)

# Tricks and Tips

- **Utility Classes** `.u-margin-right-sm { margin-right: 1.6rem !important; }`

- Selecting elements that are not hovered - `box:hoveer img:not(:hover) {}`

- [Style Checkboxes and Radio buttons](https://web.dev/learn/forms/styling-form-controls/#checkboxes-and-radio-buttons)

- Set the background image to the text color: `h1 { color: transparent; background-image: linear-gradient(), url(); -webkit-background-clip: text; }`

- **Vendor prefixes** - are a way for your browser to support new CSS features before they become fully supported in all browsers.

- `touch-action` CSS property sets how an element's region can be manipulated by a touchscreen user (e.g. zooming features built into the browser)

<br>

## Disable Text Selection

You can use the `user-select` property to disable text selection of an element.

```css
.noselect {
  -webkit-user-select: none; /* Safari */
  -ms-user-select: none; /* IE 10 and IE 11 */
  user-select: none; /* Standard syntax */
}
```

<br>

## Mobile Navigation

**Hide elements without using `display: none`**

```scss
.nav {
  opacity: 0;
  pointer-events: none; // make the element unaccessible to mouse or keyboard
  visibility: hidden; // hide the element from screen readers
}
```

**Open the navigation:**

```css
.open .nav {
  opacity: 1;
  pointer-events: auto;
  visibility: visible;
}
```

All we need to do is to toggle the `open` class on a parent element to activate or disable the styles.

**To hide the navigation on sides:**

```css
html {
  overflow-x: hidden;
}
body {
  overflow-x: hidden;
}
```

All the elements that overflow the viewport in the X axis (horizontally), will be hidden.

<br>

## Test and Optimize

- Make sure website works well in all major browsers
- Test the website on actual mobile devices, not just in DevTools
- Optimize all images, in terms of dimensions and file size
- Fix simple accessibility problems (e.g. color contrast issues)
- Run the Lighthouse performance test in Chrome DevTools and try to fix reported issues
- Think about Search Engine Optimization (SEO)

<br>
