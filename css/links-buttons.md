[&larr; Back](./README.md)

# Links and Buttons

Links are for navigating on the page, while button elements should be used for actions.

<br>

## Table of Content

- [Anchor Element](#anchor-element)
- [Skeuomorphism and Flat Design `<button>`](#skeuomorphism-and-flat-design-button)
- [Primary and Secondary Navigation](#primary-and-secondary-navigation)
  - [Breadcrumbs](#breadcrumbs)
  - [Breadcrumb Types](#breadcrumb-types)

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

Always use `link` and `visited` states for anchor tags.

<br>

## Skeuomorphism and Flat Design `<button>`

**Skeuomorphism** is a concept of UI elements that imitate real-life counterparts.

Skeuomorphic button design can be implemented using image files and CSS rules. `hover` and `active` states are important.

**Flat Design** is an alternative approach which embraces the fact that computer interface do not necessarily need to model real-live interfaces.

Elements have a flat appearance. Designers rely on other signifiers to indicate clickability. Text here is important for clarity.

In both situations, we should use `cursor: pointer` and `hover` states. Buttons should display their clickability.

<br>

## Primary and Secondary Navigation

- **Primary Navigation** system contains the most important links and buttons that need to be displayed on every single page of the site.
- **Secondary Navigation** (_breadcrumb navigation_), usually consists of a clickable list of pages that led to the current page. It help users understand the extend of the site and where they are currently.

<br>

### Breadcrumbs

Breadcrumbs - displayed as a horizontal list of pages, take up minimum space, located in the header, left-aligned and below any primary navigation. Typically separated with a `>` or a `/` symbol. Are not underlined, should change when you hover them. Provide signifier to what breadcrumb you are.

<br>

### Breadcrumb Types

- location - based on hierarchical structure of site
- attribute - based on attributes of current page or item
- path - unique to a user’s journey on the site

Path-based breadcrumbs can be confusing, only use if needed. Ensure breadcrumbs will add value before adding to a site.
