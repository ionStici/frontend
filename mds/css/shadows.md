# Shadows

## Box Shadow

**`box-shadow`** property - add shadows to boxes.

```css
.box {
  box-shadow: inset 5px 5px 20px 5px #999;
}
```

Order of values for `box-shadow`:

1. **Horizontal offset:** a positive number pushes it out from the left and a negative number will push it out from the right.
2. **Vertical offset:** a positive number pushes it down from the top, and a negative number will push it up from the bottom.
3. **Blur radius:** a larger number produces a more blurred shadow, whereas a small number produces a sharper shadow.
4. **Spread radius** (optional): a larger number increases the size of the shadow and a smaller number decreases it, making it the same size as the blur radius if it's set to 0.
5. **Color:** Any valid color value. If this isn't defined, the computed text color will be used.

**Inner shadow:** add an `inset` keyword before the other properties.

**Multiple Shadows:** you can add as many shadows as you like in one `box-shadow` property, just add a comma separated collection of values.

## Text Shadow

**`text-shadow`** property - add shadow on text nodes.

The values for `text-shadow` are the same as `box-shadow` and in the same order. The only difference is that `text-shadow` has no spread value (fourth value) and no `inset` keyword. You can add as many text shadows as you like.

```css
.box {
  text-shadow: 3px 3px 3px hotpink;
}
```

## Drop Shadow

**`drop-shadow`** filter - to achieve a drop shadow that follows any potential curves of an image.

```CSS
.box {
  filter: drop-shadow(0px 0px 10px rgba(0 0 0 / 30%))
}
```

The `drop-shadow` filter has the same values as `box-shadow`, but the `inset` keyword and `spread` value are not allowed.

You can add as many shadows as you like, by adding multiple instances of `drop-shadow` values to the `filter` property. Each shadow will use the last shadow as a positioning reference point.
