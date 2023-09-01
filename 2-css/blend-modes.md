[&larr; Back](./README.md)

# Blend Modes

**Blend Modes** - compositional effects by mixing colors from two or more layers.

- [`mix-blend-mode`](https://developer.mozilla.org/en-US/docs/Web/CSS/mix-blend-mode) applies blending to the whole element.

- [`background-blend-mode`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-blend-mode) applies blending to the background of an element.

Blend modes fall into two categories: **separable** and **non-separable**. A separable blend mode considers each color component, such as RGB, individually. A non-separable blend mode considers all color components equally.

<br>

## Separable blend modes

```scss
.box {
  mix-blend-mode: normal; // default blend mode, no blend
  mix-blend-mode: multiply;
}
```

- `multiply` lights get much lighter and darks darker, most often producing a darker result.

- `screen` inverse effect to `multiply`, will most often produce a brighter result.

- `overlay` combines `multiply` and `screen`, base dark colors become darker and base light colors become lighter.

- `darken` blend mode compares the source image and backdrop image's dark color luminosity and selects the darkest of the two.

- `lighten` does the opposite of darken.

- `color-dodge` lightens the background color to reflect the source color.

- `color-burn` increases contrast, resulting in more saturated mid-tones and reduced highlights.

- `hard-light` creates a vivid contrast.

- `soft-light` a less-harsh version of `overlay`.

- `difference` takes the difference value of each pixel, inverting light colors.

- `exclusion` similar to `difference`, but it will return 50% gray, resulting in a softer output with less contrast.

<br>

## Non-separable blend modes

You can think of these blend modes like HSL color components. Each takes a specific component value from the active layer and mixes it with other component values.

- `hue` takes the hue of the source color and applies it to the saturation and luminosity of the backdrop color.

- `saturation` applies the saturation of the source color to the hue and luminosity of the backdrop color.

- `color` will create a color from the hue and saturation of the source color and the luminosity of the backdrop color.

- `luminosity` the inverse of `color`.

<br>

## The isolation property

```css
.box {
  isolation: isolate;
}
```

[Example](https://codepen.io/web-dot-dev/pen/JjELLXy)

This will create a new stacking context, which will prevent it from blending with a backdrop layer.

The parent-level blend modes will no longer apply, but elements inside of an element with `{ isolation: isolate }` set can still blend.

_p.s._ This doesn't work with `background-blend-mode`

<br>
