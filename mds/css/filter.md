# Filter

## The filter property

```scss
.img {
  filter: blur(2px) brightness(0.8);
  filter: brightness(0) opacity(0.5); // turn imgs grey
}
```

- We can apply multiple filter values in one `filter` property.

- `blur(3px)` this applies a gaussian blur. Requries length units.

- `brightness(80%)` increase or decrease the brightness of an element (percentages or decimals).

- `contrast(160%)` decrease or increase the contrast (percentages).

- `grayscale(80%)` grayscale effect (percentages or decimals).

- `invert(1)` the element's color is inverted (percentages or decimals).

- `opacity(0.3)` works just like the `opacity` property (percentages or decimals).

- `saturate(155%)` increases or decreases color saturation (percentages or decimals).

- `sepia(70%)` sepia tone effect (percentages or decimals).

- `hue-rotate(120deg)` shifts the hue of all the element's colors (degrees).

- `drop-shadow(5px 5px 10px orange)` add shadow to a cutout image (no inset or spread values).

- `url(#pink-filter)` apply an SVG filter from a linked SVG element or file.

## Backdrop filter

The [`backdrop-filter`](https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter) property accepts all of the same filter function values as `filter.`

The difference between `backdrop-filter` and `filter` is that the `backdrop-filter` property only applies the filters to the background, where the `filter` property applies it to the whole element.
