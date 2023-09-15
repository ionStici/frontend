[&larr; back](./README.md)

# Media queries Introduction

Media queries are initiated with the `@media` keyword (a CSS at-rule), and can be used for a variety of use cases.

<br>

- **Media types** - e.g. `@media print {}`

  `print` will target prints only. We also have `screen` type only for screens.

  If you don'y specify any media type for your CSS, it will automatically have a media type value of `all`

<br>

- **Conditions** _(media features)_ - syntax: `@media type and (feature)`

  The CSS code from a media query is applied only if the media type matches and if the condition is true.

  ```css
  @media all and (orientation: landscape) { Styles for landscape mode }
  @media all and (orientation: portrait) { Styles for portrait mode }
  ```

<br>

- You can use **media queries on a `link` element** inside the `media` attribute

  `<link rel"stylesheet" href="responsive.css" media="(min-width: 500px)">`

  If the MQ matches, the style sheet will apply. Use only `@media` at-rules instead.

<br>

- **Browser Viewport Media Features**

  Features: `min-width max-width min-height max-height`

  ```css
  @media (min-width: 375px) { apply when the browser window is wider than 375px }
  ```

<br>

- Apply **multiple conditions** using the `and` keyword

  ```css
  @media (min-width: 375px) and (max-width: 600px) {
    /* styles for viewports wider than 375px and narrower than 600px  */
  }
  ```

<br>

- **Breakpoints** - the point at which a media feature condition becomes true.

  Recommendation: Choose your breakpoints based on your content rather than popular device sizes.

<br>
