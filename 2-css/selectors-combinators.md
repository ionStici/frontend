[&larr; Back](./selectors.md)

# Combinators

## Table of Content

- [Descendent Combinator](#descendent-combinator)
- [Child Combinator](#child-combinator)
- [General Sibling Combinator](#general-sibling-combinator)
- [Adjacent Sibling Combinator](#adjacent-sibling-combinator)

<br>

## Descendent Combinator

```
div p { }
```

This will target the `p` child element within `div` parent element.

<br>

## Child Combinator

```
div > p { }
```

This will select all `p` elements that are nested directly inside `div` element.

<br>

## General Sibling Combinator

```
div ~ p { }
```

This will select all `p` elements as long as they follow a `div` element.

<br>

## Adjacent Sibling Combinator

```
div + p { }
```

This will select `p` elements that directly follow a `div` element.

<br>
