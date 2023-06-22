[&larr; Back](./README.md)

# Digital Accessibility (a11y)

## Table of Content

- [ARIA and HTML](#aria-and-html)

<br>

## ARIA and HTML

**Accessible Rich Internet Applications (ARIA)** - a set of attributes we can add to HTML elements to increase their accessibility. These attributes communicate role, state, and property to assistive technologies via accessibility APIs found in modern browsers. This communication happens through the **accessibility tree**.

The **Accessibility Tree** is created by the browser and based on the DOM tree. Its purpose is to make the webpage as accessible as possible by working along with **Assistive Technologies (AT)**. The accessibility tree contains objects representing all the markup elements, attributes, and text nodes.

[View the Accessibility Tree via Chrome DevTools](https://developer.chrome.com/blog/full-accessibility-tree/)

<br>

### ARIA Features

The three main features of ARIA are: roles, properties, states/values.

**Roles** define what an element is or does on the page:

```html
<div role="button">Click</div>
```

**Properties** express characteristics or relationships to an object:

```html
<div role="button" aria-describedby="comment">Click</div>
<p id="comment">You will be redirected to anothe page!</p>
```

**States/values** define the current conditions or data values associated with the element:

```html
<div role="button" aria-pressed="false">Click</div>
```

<br>

### Five rules of ARIA

1. **Don't use ARIA** - ARIA is required only when an HTML element doesn't have accessibility support.
2. **Don't add (unnecessary) ARIA to HTML**
3. **Always support keyboard navigation** - All interactive (not disabled) ARIA controls must be keyboard accessible (`tabindex="0"`)
4. **Don't hide focusable elements** - Don't add `role="presentation"` or `aria-hidden="true"` to elements that need to have focus.
5. **Use accessible names for interactive elements** - The purpose of an interactive element needs to be conveyed to a user before they know how to interact with it.

When the browser supports an HTML tag with an implicit role with an ARIA equivalent, there is usually no need to add ARIA to the element. However, ARIA still includes many roles, states, and properties that aren't available in any version of HTML.

<br>

## Structure

### Landmarks

**Landmarks** ensure content is in navigable regions.

When sectioning off large regions of content, you can use either ARIA landmark roles or the newer HTML landmark elements to add structural context to your page.

| HTML Landmark Element | ARIA Landmark Role |
| :-------------------: | :----------------: |
|      `<header>`       |       banner       |
|       `<main>`        |        main        |
|      `<footer>`       |    contentinfo     |
|        `<nav>`        |     navigation     |
|       `<aside>`       |   complementary    |
|      `<section>`      |       region       |
|       `<form>`        |        form        |

<br>

### Headings

Heading level one `<h1>` is used for the page's highest and most important information, moving incrementally to heading level six `<h6>` for the lowest and least important information.

The sequence of the heading levels is important, we should not skip heading levels.

<br>

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

<!--
## Digital Accessibility Requirements

- Screen readers that parse a website for a user with visual impairments
- Videos on websites are closed-captioned for individuals with hearing impairments
- Images include “alt text” for individuals with visual impairments
- Websites must be navigable by keyboard for users who may not be able to operate a mouse (i.e., navigating using the “Tab” on a keyboard)

<br>

## Accessible Design

- [Toptal](https://www.toptal.com/designers/colorfilter) - design testing tool (colorblind web page filter).
- Use the right contrast so that text and colors provide good visual cues.
- Use correct text hierarchy (`<h1>` - `<h6>`) and the right font size so our content is legible.
- Consider: Easy to distinguish links / input with labels / text with background overlaid on images.

<br>

## Accessibility in Practice

Visually impaired users use screen readers to access content on the Internet.

**A screen reader** is a piece of software that provides an audio description of a web page’s content. A screen reader not only reads the visual content out loud, it also reads out element names and other attributes that make it easier for visually impaired users to navigate a web page.

**ARIA** stands for Accessible Rich Internet Applications, and refers to guidelines that make web pages accessible.

<br>

### Semantic HTML Elements

Use the appropriate tags for a given task. Native semantics of an element describes the element’s intended purpose.

For example, the `<header>` element is intended to contain introductory and navigational elements such as a logo, links, or a search bar.

[List of all semantic HTML elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

<br>

### Alt Attribute

The `alt` attribute is used to describe an image (use `alt` instead of aria-label for images).

Screen readers will read the value of the `alt` attribute out load.

`alt` attribute conventions:

- The value of alt should concisely describe the image.
- For images that are also `<a>` elements, the alt attribute should describe the source that the link targets.
- If an image conveys no information (such as a decorative border), the alt attribute should be empty, but should never be omitted.
- If an image is described by text near the image, do not duplicate the description in the alt attribute. Use an empty alt attribute instead.
- The value of an alt attribute should be no more than 150 characters.

<br>



### ARIA Role

ARIA HTML attribute `role`. The value of `role` attribute changes how a screen reader communicates the element.

- `role="complementary"` the information from an element with this attribute is complementary (or supporting) to other information.
- `role="presentation"` will instruct screen readers to skip reading unnecessary elements (like ol, ul, div, etc.).

<br>

### ARIA Properties

ARIA properties are attributes that provide additional information about elements that might not be so abvious to users of screen readers.

The property `aria-label` gives the screen reader additional information to read out loud to the user. [ARIA Techniques](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques)

<br>

-->
