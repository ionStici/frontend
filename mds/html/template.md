# Template

## External Resources

- [Web Components | MDN Guide](https://developer.mozilla.org/en-US/docs/Web/Web_Components)
- [`<template>` | web.dev Guide](https://web.dev/learn/html/template)
- [Custom Element Best Practices](https://web.dev/custom-elements-best-practices/)
- [Custom Elements v1](https://web.dev/custom-elements-v1/)
- [Declarative Shadow DOM](https://developer.chrome.com/articles/declarative-shadow-dom/)

## Table of Content

- [Introduction](#introduction)
- [The template element](#the-template-element)
- [The slot element](#the-slot-element)
- [Custom elements](#custom-elements)
- [Shadow DOM](#shadow-dom)

## Introduction

The Web Component standard is made up of three parts: _HTML templates_, _Custom Elements_, and the _Shadow DOM_.

Combined, they enable building customized, encapsulated, reusable elements that can be seamlessly integrated into existing applications, like all the other HTML elements.

Convention when naming a custom element: use lowercase letters and dashes.

## The template element

```html
<template id="template-form">
  <form>
    <input type="text" />
    <button>Click</button>
  </form>
</template>
```

The `<template>` element is used to declare fragments of HTML to be cloned and inserted into the DOM with JavaScript.

The contents of `<template>` is not rendered to the screen, it is JavaScript that will insert the content.

The contents of `<template>` are children of a [`DocumentFragment`](https://developer.mozilla.org/en-US/docs/Web/API/DocumentFragment) returned by the [`HTMLTemplateElement.content`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLTemplateElement/content) property.

To be more visible, JavaScript must be used to grab the contents and append those contents to the DOM.

```js
document.body.append(document.getElementById("template-form").content);
```

This brief JavaScript did not create a custom element. Rather, this example has appended the contents of the `<template>` into the `<body>`. The content has become part of the visible, styleable DOM.

## The slot element

We can customize content within a `<template>` using the `<slot>` element as a placeholder for other elements.

`<slot>` elements must have a `name` attribute that will act as an identifier (named slot).

```html
<template id="template-form">
  <slot name="label">
    <label>Search:</label>
  </slot>
</template>

<custom-form>
  <label slot="label">Custom label</label>
</custom-form>
```

The `slot` attribute is used to replace the contents of the `<slot>` within a `<template>`.

To assign slots, the `slot` attribute should match the value of the `name` attribute within a named slot.

If the custom element doesn't have a match for a slot, the contents of the `<slot>` will be rendered.

## Custom elements

JavaScript is required to define custom elements.

When defined, the contents of the `<custom-form>` element will be replaced by a shadow root containing all the contents of the template we associate with it.

Below, we define the custom element named `'custom-form'` by extending the `HTMLElement`:

```js
customElements.define(
  "custom-form",
  class extends HTMLElement {
    constructor() {
      super();
      const formTemplate = document.getElementById("template-form").content;
      const shadowRoot = this.attachShadow({ mode: "open" });
      shadowRoot.append(formTemplate.cloneNode(true));
    }
  }
);
```

```html
<custom-form></custom-form>
```

Now the element is defined. Every time the browser encounters a `<custom-form>` element, it will be rendered as a copy of the `<template>`.

We append a clone of the template contents to the document body each time we use the custom element (and adding the content to the regular DOM).

Note: Being part of a shadow DOM rather than the standard DOM, styles scoped to the document does not apply. We have to create encapsulated styles to style our encapsulated Shadow DOM content.

## Shadow DOM

The Shadow DOM scopes CSS styles to each shadow tree, isolating it from the rest of the document.

This means external CSS doesn't apply to your component, and component styles have no effect on the rest of the document, unless we intentionally direct them to.

We can include a `<style>` element providing encapsulated CSS to the custom element.

```html
<template>
  <style>
    .label {
      color: red;
    }
  </style>
  <form></form>
</template>
```

While web components are encapsulated with in `<template>` markup and CSS styles are scoped to the shadow DOM and hidden from everything outside of the components, the slot content which gets rendered, the `<anyElement slot="slot-id">` portion of the component, is not encapsulated.

[Styling outside of the current scope](https://web.dev/learn/html/template/#styling-outside-of-the-current-scope)
