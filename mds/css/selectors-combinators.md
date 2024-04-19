# Combinators

## Table of Content

- [Descendent Combinator](#descendent-combinator)
- [Child Combinator](#child-combinator)
- [General Sibling Combinator](#general-sibling-combinator)
- [Adjacent Sibling Combinator](#adjacent-sibling-combinator)

## Descendent Combinator

```
div p { }
```

This will target all `p` child elements **within** `div` parent element.

## Child Combinator

```
div > p { }
```

This will select all `p` elements that are **nested directly** inside `div` parent element.

## General Sibling Combinator

```
div ~ p { }
```

This will select all `p` elements as long as they follow a `div` element.

## Adjacent Sibling Combinator

```
div + p { }
```

This will select the `p` element that **directly follows** a `div` element.
