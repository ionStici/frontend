[&larr; Back](./README.md)

# Digital Accessibility (a11y)

## Table of Content

- [ARIA and HTML](#aria-and-html)
- [Structure](#structure)
- [The Document](#the-document)
- [Focus](#focus)
- [JavaScript](#javascript)
- [Images](#images)
- [Accessible Design](#accessible-design)
- [Animation and Motion](#animation-and-motion)
- [Typography](#typography)
- [Automated Accessibility Testing](#automated-accessibility-testing)
- [Manual Accessibility Testing](#manual-accessibility-testing)
- [Assistive Technology testing](#assistive-technology-testing)

<div></div>

**External Resources:**

- [A11y Checklist](https://www.a11yproject.com/checklist/)

<br>

## ARIA and HTML

**Accessible Rich Internet Applications (ARIA)** - a set of attributes we can add to HTML elements to increase their accessibility. These attributes communicate role, state, and property to assistive technologies via accessibility APIs found in modern browsers. This communication happens through the **accessibility tree**.

The **Accessibility Tree** is created by the browser and based on the DOM tree. Its purpose is to make the webpage as accessible as possible by working along with **Assistive Technologies (AT)**. The accessibility tree contains objects representing all the markup elements, attributes, and text nodes.

[View the Accessibility Tree via Chrome DevTools](https://developer.chrome.com/blog/full-accessibility-tree/)

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

### Five rules of ARIA

1. **Don't use ARIA** - ARIA is required only when an HTML element doesn't have accessibility support.
2. **Don't add (unnecessary) ARIA to HTML**
3. **Always support keyboard navigation** - All interactive (not disabled) ARIA controls must be keyboard accessible (`tabindex="0"`)
4. **Don't hide focusable elements** - Don't add `role="presentation"` or `aria-hidden="true"` to elements that need to have focus.
5. **Use accessible names for interactive elements** - The purpose of an interactive element needs to be conveyed to a user before they know how to interact with it.

When the browser supports an HTML tag with an implicit role with an ARIA equivalent, there is usually no need to add ARIA to the element. However, ARIA still includes many roles, states, and properties that aren't available in any version of HTML.

### ARIA Role

ARIA HTML attribute `role`. The value of `role` attribute changes how a screen reader communicates the element.

- `role="complementary"` the information from an element with this attribute is complementary (or supporting) to other information.
- `role="presentation"` will instruct screen readers to skip reading unnecessary elements (like ol, ul, div, etc.).

### ARIA Properties

ARIA properties are attributes that provide additional information about elements that might not be so abvious to users of screen readers.

The property `aria-label` gives the screen reader additional information to read out loud to the user. [ARIA Techniques](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques)

<br>

## Structure

### Semantic HTML Elements

Native semantics of an element describes the element’s intended purpose.

[List of all semantic HTML elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

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

### Headings

Heading level one `<h1>` is used for the page's highest and most important information, moving incrementally to heading level six `<h6>` for the lowest and least important information.

The sequence of the heading levels is important, we should not skip heading levels.

<br>

## The Document

### Page Title

Page `<title>` is displayed in the browser tab, it helps users understand which page they are visiting. It should be equivalent to the `<h1>` or main topic of the page.

For SPAs, the page title is updated using `document.title`

Descriptive page titles are good for both Users and SEO. The title is the first thing announced when an AT user visits a page. The title must be accurate, unique, descriptive, concise, but also not too much keywords.

Btw, Search engines typically display only the first 55–60 characters of a page title.

### Language

**Page Language**: `<html lang="en">` the default language for the entire page.

**Section Language**: `<section lang="en">` this will override the top-level language setting for a specific section of content.

<br>

## Focus

[**Focus Lesson**](./focus.md)

- <kbd>tab</kbd> key moves the keyboard focus up the DOM.
- <kbd>shift + tab</kbd> moves the focus down the DOM.

### Skip Links

**Skip links** (typically the first focusable element) are anchor links that jump to a different section of the same page, using that section's ID.

When a user presses the tab key, and an active skip link is in place, it sends the keyboard focus to the skip link. The user can click the skip link and jump past the header section and main navigation.

```html
<a href="#content" class="skip">Skip to main content</a>
```

```css
.skip {
  display: none;
}

.skip:focus {
  display: block;
}
```

### Focus indicator

- Default CSS property for style elements with focus: `outline`
- Important: Set an appropriate highlighting style for focusable elements.
- Recommendation: 3:1 color contrast ratio for all focus indicators.

<br>

## JavaScript

- **Important:** Besides click events, add appropriate key events (e.g. enter) to focusable elements.
- When transitioning between pages (or routing), decide where the focus goes.
- Instead of adding inline styles, better toggle CSS classes.

### State Management

[ARIA states and properties](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes)

**Component level**

- `aria-expanded` attribute tells the user whether a drop-down menu or list is expanded or collapsed.
- `aria-pressed` can indicate if a button has been pressed.

<br>

## Images

- Decorative images that are presentational should be applied with CSS (no context).
- When an image adds context to a document, it is content and should be embedded with HTML.

<div></div>

- **What is the image purpose?** Inform / Enrich
- **What are the next steps?** Message / Action
- **What is the message?** Simple / Complex / Emotional

<div></div>

### Decorative Images

A _decorative image_ is a visual element that doesn't add information for users to better understand the context.

If an image is decorative, it must be programmatically hidden from ATs, examples:

1. Empty/null text alternative `alt=""`

2. Applying ARIA:

   `role="presentation" role="none"` this removes an element's semantics from exposure to the accessibility tree.

   `aria-hidden="true"` this removes the entire element - and all of its children - from the accessibility API.

3. Add the image as a CSS background.

### Informative Images

An _informative images_ is an image that conveys an idea, emotion, or a simple concept, examples: photos of real-world objects, icons, drawings, images of text.

If the image is informative, we should include programmatic alternative text describing the purpose of the image `alt` (regardless of the file type).

The `alt` attribute will give to AT users more context about an image and help them better understand an image's message.

In case the image is of SVG type, we also should include the `role="img"` attribute, so that ATs will recognize it as an image.

### Functional Images

A _functional image_ is connected to an action. Examples: an logo that links to the home page, a magnifying glass used as a search button, or a social media icon that directs you to a different website or app.

Unlike an informative image, the functional image's `alt` attribute needs to describe the image's action (not the visual aspects). But, it is not a requirement.

### Complex images

_Complex Image_ - infographics, maps, graphs/charts, and complex illustrations.

1. One way to add additional explanation to an image is to link out to a resource or provide a jump link to a longer explanation later on the page.

2. Use `aria-describedby="id"` on the img element, this will link the image to an ID containing a longer description, this will create a strong association between the image and the full description.

3. Use `<figure>` and `<figcaption>` elements to group short alternative descriptions with a longer one.

### Alt Attribute Conventions

- Use proper punctuation, avoid non-alpha characters, use dashes instead of underscores.
- The value of `alt` should concisely describe the image.
- For images that are also `<a>` elements, the alt attribute should describe the source that the link targets.
- If an image conveys no information (such as a decorative border), the alt attribute should be empty, but should never be omitted.
- If an image is described by text near the image, do not duplicate the description in the alt attribute. Use an empty alt attribute instead.
- The value of an alt attribute should be no more than 150 characters.

<br>

## Accessible Design

- [Toptal](https://www.toptal.com/designers/colorfilter) - design testing tool (colorblind web page filter).
- Use the right contrast so that text and colors provide good visual cues.
- Use correct text hierarchy (`<h1>` - `<h6>`) and the right font size so our content is legible.
- Consider: Easy to distinguish links / input with labels / text with background overlaid on images.
- Use `@prefers-color-scheme` media query to allow users to choose a light or dark theme version of the website based on their OS settings.

<br>

## Animation and Motion

- Avoid flashes.
- If the element's animation is not essential, consider not using it then.
- Use `@prefers-reduced-motion` media query that checks the user's OS settings related to animation.
- Add a toggle to turn _on_ or _off_ animations. Consider defaulting the toggler to _off_.

<br>

## Typography

The quickiest way to create an accessible design is to choose a common typeface, ex: Arial, Times New Roman, Calibri, Verdana.

- Avoid using elaborate or handwritten fonts and those with only one character case.
- Limit the number of typeface variations like color, bold, ALL CAPS, and italics to increase readability.
- Use markup instead of text on images whenever possible.
- Base font sizes should be defined with a relative value (%, rem, or em) to allow easy resizing.

An important aspect of accessible layout designs is making critical elements distinct from one another and grouping similar elements together. If the elements are too close, it can be difficult to tell where one element begins and ends, especially if they have similar styling.

Tools: [Good Line-Height](https://www.thegoodlineheight.com/) & [Golden Ratio Calculator](https://grtcalculator.com/)

- Use elements like headings, subheadings, lists, numbers, quote blocks, and other visual groupings to break the page into sections.
- Use clearly defined paragraphs, sentences, and word spacing.
- Build columns of copy that do not exceed 80 characters in width (40 characters for logograms).
- Avoid justified paragraph alignment.

<br>

## Automated Accessibility Testing

**Lighthouse** is an open-source, automated tool created to improve the quality of web pages through different types of audits, such as performance, SEO, and accessibility.

<br>

## Manual Accessibility Testing

[Manual a11y checklist (IBM)](https://www.ibm.com/able/toolkit/verify/manual/)

Focus areas: keyboard functionality, visually-focused reviews, general content checks.

**Essential commands for keyboard testing:**

| Key              | Result                                       |
| :--------------- | :------------------------------------------- |
| Tab              | Moves forward one active element to another  |
| Shift + Tab      | Moves backward one active element to another |
| Arrows           | Cycle through related controls               |
| Spacebar         | Toggles states and moves down the page       |
| Shift + Spacebar | Moves up the page                            |
| Enter            | Triggers specific controls                   |
| Escape           | Dismisses dynamically displayed objects      |

<br>

## Assistive Technology testing

**A screen reader** is a piece of software that provides an audio description of a web page’s content. A screen reader not only reads the visual content out loud, it also reads out element names and other attributes that make it easier for visually impaired users to navigate a web page.

- Best Screen Reader for iOS and MacOS devices: _VoiceOver_.
- [Screen reader testing demo](https://web.dev/learn/accessibility/test-assistive-technology/)

<br>
