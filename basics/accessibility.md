# Digital Accessibility

## Table of Content

- [Accessibility Overview](#accessibility-overview)
- [Accessible Design](#accessible-design)
- [Accessibility in practice](#accessibility-in-practice)
  - [Semantic HTML Elements](#semantic-html-elements)
  - [Alt Attribute](#alt-attribute)
  - [ARIA Role](#aria-role)
  - [ARIA Properties](#aria-properties)

External Resoruces:

- [CSS and JavaScript accessibility best practices by MDN](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/CSS_and_JavaScript)
- [The a11y Project Checklist](https://www.a11yproject.com/checklist/)

<br>

## Accessibility Overview

**Accessibility** refers to designing devices. products, environments - so that individuals with disabilities or sensory impairments can successfully use the device or product.

**Digital Accessibility** refers specifically to digital media (not much different from the general idea of accessibility).

**Digital Accessibility Requirements:**

- Screen readers that parse a website for a user with visual impairments
- Videos on websites are closed-captioned for individuals with hearing impairments
- Images include “alt text” for individuals with visual impairments
- Websites must be navigable by keyboard for users who may not be able to operate a mouse (i.e., navigating using the “Tab” on a keyboard)

Recommendations for making Web content more accessible [Web Content Accessibility Guidelines 2.1](https://www.w3.org/TR/WCAG21/)

<br>

## Accessible Design

- [Toptal](https://www.toptal.com/designers/colorfilter) - design testing tool (colorblind web page filter).
- Use the right contrast so that text and colors provide good visual cues.
- Use correct text hierarchy (`<h1><h6>`) and the right font size so our content is legible.
- Consider: Easy to distinguish links / input with labels / text with background overlaid on images.

<br>

## Accessibility in practice

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
