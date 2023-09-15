[&larr; Back](./README.md)

# Sass Features

## Table of Content

- [Sass Variables](#sass-variables)
- [Sass Nesting](#sass-nesting)
- []()

<br>

## Sass Variables

Defining and Using a Sass variable:

```
$color-text: #333;
p { color: $color-text; }
```

<br>

## Sass Nesting

- The `&` ampersand symbol in Sass acts as an selector that follow the path from the root until its current location in the nesting system.

  In Sass, it is handy to user `&` for pseudo-classes, e.g. `button { &:hover { } }`

```scss
div {
    li {
        &:first-child {..}
        a:link {..}
    }
}
```

After compiling, the code above will result in:

```
div {}
div li {}
div li:first-child {}
div li a:link {}
```

There is no limit how fat we can nest, however you shouldn't go deeper than the third level.

Other useful way of using nesting, is by combining it with the BEM methodology:

```scss
.header {
  &__logo {
  }
}
```

Here, `&` replaces the `header` word and targets the `header__logo` class, allowing us to create self-contained code blocks.

<br>
