# BEM Methodology

**BEM:** Consistent strategy and structure for naming our classes.

**BEM** stands for **Block** -> **Element** -> **Modifier**.

- **Block** is a standalone component that is meaningful on its own.

  We name these standalone components with meaningful words like: `recipe` or `header`

<div></div>

- **Element** is a part of a _block_ and has no standalone meaning on its own.

  We name these parts starting with the _block_ name, then 2 underscores, and then the element name itself.

  Example: `header__text-box`

<div></div>

- **Modifier** - is a flag that adds a minor change to the regular styles of the element.

  Example: `btn--green`

```
.block {}
.block__element {}
.block__element--modifier {}
```

We use only classes as selectors, which have low-specificity.
