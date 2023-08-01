[&larr; Back](./README.md)

# How CSS works behind the scenes

## Table of Content

- [CSS Object Model](#css-object-model)
- [The Visual Formatting Model](#the-visual-formatting-model)
- [The Cascade](#the-cascade)
- [Specificity](#specificity)
- [Inheritance](#inheritance)

<br>

## CSS Object Model

The browser starts to load and parse the HTML file, then decodes the HTML code and builds the Document Object Model (DOM), which describes the entire web document in a tree-like structure.

As the browser parses the HTML document, it finds the `link` tag in the HTML head and it starts to load and parse the CSS file as well.

During the CSS parsing phase, two main steps take place:

- **Step 1** - Conflicting CSS declarations are resolved through a process known as **cascade**
- **Step 2** - Processing final CSS values, converting relative units to pixels

The final CSS is also stored in a tree-like structure, called the **CSS Object Model (CSSOM)**. The parsed and stored HTML document and CSS file together form the **Render Tree**, which then renders the page.

In order to render the page, the browser uses an algorithm called the **Visual Formatting Model** that calculates and uses a bunch of stuff like box-model, floats, and positioning.

After the Visual Formatting Model has done its works, the website is finally displayed to the screen, and the process is finished.

<br>

## The Visual Formatting Model

**The Visual Formatting Model** is an algorithm that determines the overall layout by calculating the dimensions of each element in the render tree.

The algorithm takes in account:

- Box dimensions (the box model) and Box types (set by `display`)
- Positioning scheme (normal flow, float, absolute positioning)
- Stacking Contexts and Other elements present in the document tree
- External information such as viewport size, intrinsic dimensions of images, etc.

All these concepts together determine how the website will look in the browser.

<br>

## The Cascade

The **cascade** is the algorithm for solving conflicts where multiple CSS rules apply to an HTML element.

The cascade algorithm is split into 4 distinct stages:

1. **Position and order of appearance:** the order of which the CSS rules appear
2. **Specificity:** an algorithm which determines which CSS selector has the strongest match
3. **Origin:** the order of when CSS appears and where it comes from
4. **Importance:** some CSS rules are weighted more heavily than others `!important`

### 1. Position and order of appearance

- Two selectors of identical specificity: the last one written in the code is the one that will apply.
- The same CSS property declared multiple times in the same selector: the last one declared will apply.

<div></div>

- Multiple CSS files linked via the `<link>` tag: the last `<link>` will have the most specificity.
- If the `<style>` element is declared before a `<link>`: the linked stylesheet's CSS will have the most specificity.
- An inline `style` attribute with CSS declared in it will override all other CSS, regardless of its position, unless a delcaration has `!important` defined.

<div></div>

Being able to specify two values for the same property can be a simple way to create fallbacks for browsers that do not support a particular value. This approach of declaring the same property twice works because browsers ignore values they don't understand. Unlike some other programming languages, CSS will not throw an error or break your program when it detects a line it cannot parse—the value it cannot parse is invalid and therefore ignored. The browser then continues to process the rest of the CSS without breaking stuff it already understands.

### 2. Specificity

**Specificity** is an algorithm which determines which CSS selector is the most specific. Some selectors are more specific than others:

- Inline styles > IDs > Classes > Elements

Inline styles will override IDs, and IDs will override classes, and then classes will override elements, and the reason for this behavior is that each selector type has a different level of specificity.

**Specificity is cumulative:** each type of selector is awarded points which indicate how specific it is, the points for all of the selectors you have used to target an element are added together.

### 3. Origin

The CSS that you write isn't the only CSS applied to a page. The cascade takes into account the origin of the CSS. This origin includes the browser's internal stylesheet, styles added by browser extensions or the operating system, and your authored CSS. The **order of specificity of these origins**, from least specific, to most specific is as follows:

1. **User agent base styles**. These are the styles that your browser applies to HTML elemnets by default.
2. **Local user styles**. These can come from the operating system level, such as a base font size, or browser extension level CSS.
3. **Authored CSS**. The CSS that you (the developer) author.
4. **Authored `!important`**. Any `!important` that you add to your authored declarations.
5. **Local user styles `!important`**. Any `!important` that come from the operating system level, or browser extension level CSS.
6. **User agent `!important`**. Any `!important` that are defined in the default CSS, provided by the browser.

[Order of Specificity based on Origin](https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/zPdaZ6G11oYrgJ78EfF7.svg)

<!-- 1. The most important declarations - are the user declarations marked with the !important keyword;
2. Second: the author declarations marked with the !important keyword;
3. Third: the normal author declarations;
4. Then, normal user declarations;
5. The least important ones - the browser declarations; -->

### 4. Importance

The cascade gives the conflicting declarations different importance based on where they are declared (source).

The **order of importance**, from least important, to most important is as follows:

1. normal rule type (properties)
2. `animation` rule type
3. `!important` rule type (properties)
4. `transition` rule type

Active animation and transition rule types have higher importance than normal rules. In the case of transitions higher importance than `!important` rule types. This is because when an animation or transition becomes active, its expected behaviour is to change visual state.

<br>

## Specificity

Each selector gets a scoring. **Specificity = total score for a selector rule**.

Each selector type earns points. You add all of these points up to calculate a selector's overall specificity.

- `*` universal selector has no specificity / gets 0 points, any rule with 1 or more will override it
- **Element** or **pseudo-element** selector gets **1 point** of specificity
- **Class, pseudo-class, attribute** selector gets 10 points of specificity
- An **ID** selector gets 100 points of specificity
- CSS applied directly to the `style` attribute of the HTML element, gets a **specificity score of 1000 points**
- An `!important` at the end of a CSS value gets a specificity score of **10.000 points**

When a selector rule is composed of multiple selectors, the specificity of each individual selector is added to the overall score of the selector rule, e.g. `a.link {}` an element and a class selector will have together 11 points of specificity.

**Best practice rule:** use mostly only classes as selectors and rely on order of appearance.

<br>

## Inheritance

<br>
