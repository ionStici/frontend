# How CSS works behind the scenes

## Table of Contents

- [CSS Object Model Explained](#css-object-model-explained)
- [Understanding the Visual Formatting Model](#understanding-the-visual-formatting-model)
- [The Cascade Explained](#the-cascade-explained)
- [Understanding Specificity in CSS](#understanding-specificity-in-css)
- [Understanding CSS Inheritance](#understanding-css-inheritance)

## CSS Object Model Explained

When a browser loads a web page, it begins by parsing the HTML file to decode its contents and constructs the Document Object Model (DOM). The DOM represents the entire structure of the web document as a hierarchical tree.

While processing the HTML, the browser identifies `link` tags within the HTML's head section and subsequently loads and parses associated CSS files. Parsing the CSS involves two primary phases:

1. **Resolution of Conflicts:** Conflicting CSS declarations are resolved using a mechanism called the **cascade**.
2. **Finalization of CSS values:** Processing final CSS values, converting relative units to pixels.

The outcome of CSS parsing is the **CSS Object Model (CSSOM)**, a tree-like structure that maps styles to the corresponding elements in the DOM. The combination of the DOM and CSSOM forms the **Render Tree**, which the browser uses to visually render the page.

The rendering process employs the **Visual Formatting Model**, an algorithm that calculates layout based on several factors, including the box model, element floats, and positioning. Once this model completes its calculations, the page is displayed on the screen.

## Understanding the Visual Formatting Model

The **Visual Formatting Model** is crucial for determining the spatial arrangement of elements within the render tree. It considers several factors:

1. **Box dimensions and types:** Determined by the `display` property and the box model.
2. **Positioning schemes:** Includes normal flow, floating elements, and absolute positioning.
3. **Stacking Contexts:** Determines the layering of elements.
4. **External factors:** Such as the viewport size and intrinsic dimensions of content like images.

These factors collectively influence the final appearance of a website in a browser, defining how elements are laid out and interact visually.

## The Cascade Explained

The **cascade** is an essential algorithm in CSS that resolves conflicts when multiple CSS rules target the same HTML element. This process is divided into four key stages:

1. **Position and Order or Appearance:** the order of which CSS rules appear.
2. **Specificity:** algorithm that determines which CSS selector has the strongest match.
3. **Origin:** where CSS comes from
4. **Importance:** some CSS declarations are weighted more heavily than others

### 1. Position and Order of Appearance

In Situations where CSS selectors have identical specificity, the selector that appears last in the CSS source is applied. This holds true for:

- Selectors within the same stylesheet: the last written takes precedence.
- Multiple CSS rules in the same selector: the last declared rule is the one applied.
- Multiple stylesheets linked in the HTML: the last stylesheet linked overrides earlier ones.
- Inline styles: these always take precedense over external stylesheets unless overridden by `!important`

Moreover, CSS allows the same property to be declared multiple times within a selector to provide fallbacks for unsupported values. Browsers will ignore unsupported values and apply the next valid declaration.

### 2. Specificity

**Specificity** is a measure used to determine which CSS rules is more precise and therefore should be applied. The specificity hierarchy is as follows:

- **Inline Styles:** have the highest specificity.
- **IDs:** are mote specific than classes.
- **Classes:** have greater specificity than element selectors.

Specificity is cumulative; it's calculated by adding the points from each type of selector in a rule. This system ensures that the more specific a selector, the higher its priority in the cascade.

### 3. Origin

CSS can originate from various sources, not just the source code. The cascade accounts for these origins in a specific order, considering their specificity:

1. **User agent stylesheet:** The default styles applied by the browser.
2. **User styles:** Styles set by the user's operating system or browser extensions.
3. **Author styles:** Styles written by the website's developer.
4. **Author styles with `!important`:** Overrides all other styles except user `!important` declarations.
5. **User styles with `!important`:** Overrides all other styles, including author `!important`.
6. **User agent styles with `!important`:** Rarely used but would override all other styles.

### 4. Importance

The cascade assigns different levels of importance to CSS declarations based on their source and type:

1. **Normal rules:** Standard CSS properties.
2. **Animations:** Override normal rules due to their dynamic nature.
3. **`!important` rules:** Typically override all other types unless more specific.
4. **Transitions:** These have unique behaviors and can override even `!important` rules during their active phase.

Animations and transitions are designed to temporarily alter the visual state of elements and are given higher precedence to ensure that their effects are visible and override other static styles when active. This system ensures that dynamic styles function as expected without being blocked by higher-specificity static styles.

## Understanding Specificity in CSS

Specificity is a CSS mechanism that determines which style rules apply to an element when multiple rules could potentially match. It assigns a numeric score to each selector in a rule based on its type, and these scores are totaled to calculate the rule's overall specificity.

### Specificity Scoring System

Each type of selector contributes a different amount of points to a rule's total specificity:

- **Universal selector `*`** carries **0 points**; it has the lowest specificity.
- **Element selectors** and **pseudo-element selectors** each add **1 point**.
- **Class selectors**, **pseudo-class selectors**, and **attribute selectors** each contribute **10 points**.
- **ID selectors** provide a substantial **100 points**.
- Styles defined in the **inline `style` attribute** of an HTML element have a very high specificity of **1,000 points**.
- Declaring a style as **`!important`** in a CSS rule escalates its specificity dramatically to **10,000 points**.

### Calculating Specificity

When a selector is composed of multiple types, the points from each are added together to determine its total specificity. For example, the selector `a.link {}` combines an element selector (`a`) and a class selector (`.link`), resulting in a specificity score of 11 points (1 point for the element + 10 points for the class).

### Practical Tips on Specificity

- **Best Practices:** Generally, it's advisable to use class selectors for styling due to their moderate specificity, which makes styles easier to manage and override if necessary.
- **Avoid Over-Specificity:** Relying heavily on ID selectors or inline styles can make your CSS difficult to maintain, as these styles are harder to override due to their high specificity.
- **Use of `!important`:** This should be reserved for exceptional cases where a style must override all others. Frequent use can lead to a specificity war within your stylesheets, making them chaotic and hard to debug.

By understanding and wisely managing specificity, developers can create more flexible, maintainable, and scalable CSS architectures, avoiding common pitfalls that lead to overly complex stylesheets.

## Understanding CSS Inheritance

**Inheritance** in CSS refers to the process by which certain CSS property values set on parent elements are passed down to their child elements. This mechanism is crucial for maintaining consistency across visual elements without having to explicitly define styles for every element.

### How Inheritance Works

Not all CSS properties are inheritable, but those that typically relate to text formatting, such as `color`, `font-family`, `font-size`, and others, often are. For instance, if the `color` property is defined on the `body` element, it naturally cascades to all text elements within the `body`, unless a more specific rule overrides it.

Inheritance operates strictly in a top-down manner from parent to child. Each HTML element also possesses default values for every CSS property, known as the initial value. These initial values come into play when no specific, inherited, or default browser styles are applicable.

### Effects of Inheritance

Inheritable properties ensure that child elements can automatically adopt the computed values of their parents. For example, setting `font-weight: bold` on a parent element will cause all its child elements to display bold text unless they explicitly have a different `font-weight` set.

### Utilizing Inheritance Keywords

CSS provides several keywords to manage inheritance behaviors explicitly:

- **`inherit`:** This keyword forces a property to take the same computed value as its parent. For example, `button { color: inherit; }` ensures that the button's text color is the same as its parent element's color.
- **`initial`:** Using this keyword resets a property to its initial value as defined in CSS specifications. For example, `button { color: initial; }` would reset the button's color to the default color typically black or browser-defined, depending on the user agent.
- **`unset`:** This keyword acts differently based on whether the property is inheritable:

  - For inheritable properties, `unset` behaves like `inherit`, meaning it will take the parent's computed value.
  - For non-inheritable properties, `unset` acts like `initial`, resetting the property to its default value.

Understanding and properly using these keywords can significantly enhance CSS management by providing more control over how styles are applied and inherited across a website, making it easier to maintain a consistent look and feel while minimizing the need for redundant code.
