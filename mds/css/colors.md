# Colors

Four types of colors in CSS: Named / Hex / RGB / HSL.

We should choose one and be consistent throughout our CSS.

## Table of Content

- [Foreground and Background in CSS](#foreground-and-background-in-css)
- [Hexadecimal](#hexadecimal)
- [RGB Colors](#rgb-colors)
- [Hex and RGB](#hex-and-rgb)
- [HSL](#hsl)
- [Opacity and Alpha](#opacity-and-alpha)

## Foreground and Background in CSS

```css
h1 {
  color: grey; /* foreground color */
  background-color: red; /* background color */
}
```

## Hexadecimal

**Hex colors** - hexadecimal color system.

A hex color starts with a hash **#** and is followed by 3 or 6 characters representing values for red, blue and green.

The hexadecimal number system has 16 digits (from 0 to 15). To represent 10 - 15 digits, we use **A B C D E F**.

We can represent hex colors with 3 characters in case that it contains pairs. For example: `#00FFFF` can be written as `#0FF`.

Colors from _white_ to _black_: `fff -> eee -> ddd -> ccc -> bbb -> aaa -> 999 -> 888 -> … -> 111 -> 000`

## RGB Colors

RGB color system. RGB uses decimal numbers.

```css
h1 {
  color: rgb(43, 213, 92);
}
```

Each of the 3 values represents a color component, which have to be a decimal number value **from 0 to 255**

Besides numbers, we can use percentages to define the color spectrum: `rgb(50%, 25%, 0%)`

The first number represents the amount of red, the second is green, and the third is blue.

These colors are exactly the same as hex, but with a different syntax and a different number system.

RGB color system is convenient because it's very close to how computers represent colors internally.

## Hex and RGB

Hex and RGB syntaxes, each have 3 values, one for each color. Each can be one of 256 values.

Specifically, `256 * 256 * 256 = 16.777.216` this is the amount of colors we can represent.

## HSL

Another color system: _hue-saturation-lightness_ abbreviated as **HSL**

```css
h1 {
  color: hsl(150, 70%, 50%);
}
```

- The first number represents the degree of the hue, **from 0 to 360**.
- The second and third numbers are percentages representing saturation and lightness.

_Hue_ refers to an angle on a [color wheel](https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ob7MTste1Obu9AoLvbKq.svg). Red is `0` degrees, Green is `120` degreens, Blue is `240` degrees, then black to red is `360`. HSL is convenient for adjusting colors.

_Saturation_ refers to the intensity of the color.

_Lightness_ refers to how light or dark the color is. `50%` is normal lightness.

## Opacity and Alpha

```css
h1 {
  color: transparent;
}
```

CSS keyword for transparent color.

### Opacity in HSL

```css
h1 {
  color: hsla(34, 100%, 50%, 0.1);
}
```

The fourth value is the _alpha_, called opacity.

Alpha is a decimal number from `0` to `1`, so from transparent to opaque.

### Opacity in RGB

```css
h1 {
  color: rgba(214, 42, 91, 0.67);
}
```

RGB color system and alpha `rgba()`.

### Hex and alpha

```css
h1 {
  color: #50bc8090;
}
```

We can change the opacity of a hex color by adding a two-digit hexadecimal value to the end of the hex color (or a one-digit pair value).

Hex opacity ranges from 00 (transparent) to FF (opaque).
