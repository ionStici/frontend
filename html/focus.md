# Focus

- **`tabindex`** global attribute enable an element to receive focus.

  - `-1` a negative value makes an element focusable but not tabbable.
  - `0` will make the element focusable and reachable via tabbing (default tab order, recommended).
  - A value of `1` or more puts the element into a prioritized focus sequence (not recommended).
  - If a document includes elements with a `tabindex` of `1` and more, tabbing begins in a separate sequence, from lowest value to highest value, before going through those in the regular sequence in source order.

<br>

- **`contenteditable`** (enumerated) attribute will make an element editable, focusable, with `tabindex` set to `0`.

  - For nested `contenteditable` elements, `tabindex="0"` must be defined manually.

<br>

- **`disabled`** boolean attribute makes form controls unfocusable.

  - Disabled form controls can't be focused, don't get click events, and are not submitted upon form submission.
  - `disabled` applies to form-associated custom elements.
  - Elements that support `disabled`, are targetable with `:disabled` and `:enabled` pseudo-classes.
  - To re-enable a disabled element, the attribute has to be removed, generally via `removeAttribute()`
  - The `input.disabled` property allows you to check if an input is disabled.

<br>

- **`inert`** global boolean attribute.

  - `inert` will make an element and all nested content disabled and removed from the accessibility tree.
  - The `inert` attribute provides no visual indicators. Advice: Make inertness very apparent via CSS.

<br>

## JavaScript focus related notes

- `element.focus()` JavaScript method sets focus on the specified element (if it can be focused).

- `document.activeElement` read-only property returns the element within the DOM that currently has focus.

<br>
