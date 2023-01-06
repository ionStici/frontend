[&larr; Back](./selectors.md)

# Combinators

## Table of Content

- [Descendent Combinator]()
- [Child Combinator]()
- [General Sibling Combinator]()
- [Adjacent Sibling Combinator]()

<br>

## Descendent Combinator

```
div p { }
```

This will target the `p` element within `div` element.

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
