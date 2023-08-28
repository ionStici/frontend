[&larr; Back](./README.md)

# Gradients

## Talbe of Content

- [Linear gradient](#linear-gradient)
- [Radial gradient](#radial-gradient)
- [Conic gradient](#conic-gradient)

<div></div>

- [A Complete Guide to CSS Gradients | CSS Tricks](https://css-tricks.com/a-complete-guide-to-css-gradients/)

<br>

## Linear gradient

```css
.grad {
  background: linear-gradient(45deg, darkred 20%, darkorange 60%, gold);
}
```

The `linear-gradient()` function generates an image of two or more colors, progressively.

We can pass an angle or keyword for specific direction as first argument, e.g. `to right left` or `45deg`

We can add as many colors and color stops as we like.

The percentage next the color argument represents the size of the gradient where the color changes.

Also, we can layer gradients on top of each other by separating each gradient with a comma.

<br>

## Radial gradient

The `radial-gradient()` function - gradient that radiates in a circular fashion.

Instead of an angle, here optionally specify a position and ending shape.

If you just specify colors, the `radial-gradient()` will auto-select the position as `center` and select either a circle or ellipse, depending on the size of the box.

```css
.grad {
  background: radial-gradient(
    closest-side,
    darkorange 60%,
    gold,
    bisque,
    darkred 20%,
    crimson
  );
}
```

The size of the radial gradient determines the size of the gradient's ending shape (circle or ellipse) and by default will be `farthest-corner`, which means it exactly meets the farthest corner of the box from the center. Other Keywords:

- `closest-corner` will meet the closest corner to the center of the gradient.
- `closest-side` will meet the side of the box closest to the center of the gradient.
- `farthest-side` will do the opposite to closest-side.

<br>

## Conic gradient

A conic gradient has a center point in your box and starts from the top (by default), and goes around in a 360 degree circle.

The `conic-gradient()` function accepts position and angle arguments.

```css
.grad {
  background: conic-gradient(
    gold 20deg,
    lightcoral 20deg 190deg,
    mediumturquoise 190deg 220deg,
    plum 220deg 320deg,
    steelblue 320deg
  );
}
```

A good use case for this capability, with conic gradients is rendering pie charts with CSS.

<br>
