[&larr; Back](./README.md)

# Text and Typography Properties

- Declare your font styles on the `body`, because font properties are inherited from the parent.

- **`font-family`** set the text typeface. Accepts a comma-separated list of font families.

  Use [safe fallbacks](https://www.cssfontstack.com/) that corresponds to the same font stack.

- **`font-size`** change the size of text elements. Accepts: keywords, length units and percentages

- **`font-weight`** set the boldness of text. Numeric values: `100` to `900`

- **`font-style`** set whether a font should be styled with a `normal`, `italic`, or `oblique` face

- **`line-height`** space between text lines (unitless values)

- **`letter-spacing`** horizontal space between characters (length values)

- **`word-spacing`** space between words in a text (length values)

- **`{ font: 400 16px / 1.5 oblique serif; }`** shorthand property.

- **`text-transform`** transform text to `uppercase`, `lowercase` or `capitalize`

- [**`text-decoration`**](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration) shorthand property sets the appearance of decorative lines on text

- **`text-indent`** add indent to blocks of text (length values)

- **`text-align`** align text horizontally in a block. Keywords `left right center justify`

- [**`white-space`**](https://developer.mozilla.org/en-US/docs/Web/CSS/white-space) how white space inside an element is handled.

- **`word-break`** how words break when they would overflow the line.

- [**`vertical-align`**](https://developer.mozilla.org/en-US/docs/Web/CSS/vertical-align) sets vertical alignment of inline text.

- **`direction`** set the direction of text. `ltr` for left to right, and `rtl` for right to left.

  [Use the HTML attribute `dir` instead of the CSS `direction` property.](https://stackoverflow.com/questions/5375799/direction-ltr-rtl-whats-the-difference-between-the-css-direction-and-html-di/5375907#5375907)

- [**`writing-mode`**](https://developer.mozilla.org/en-US/docs/Web/CSS/writing-mode) change the way text flows and is arranged. Default is `horizontal-tb`

- **`text-orientation`** orientation of characters. Keywords `mixed` and `upright`.

  `text-orientation` works only when `writing-mode` ≠ `horizontal-tb`

- **`text-shadow`** add shadow to text.

- [Introduction to variable fonts on the web](https://web.dev/variable-fonts/)

- [**`font-variant`**](https://developer.mozilla.org/en-US/docs/Web/CSS/font-variant) set font variants like `small-caps` and `slashed-zero`

<br>

<!--

## Web Fonts

Web Fonts - a lot of different fonts found on the web.

Free font services: [Google Fonts](https://fonts.google.com/) and [Adobe Fonts](https://fonts.adobe.com/) - they host fonts which we can link to from our HTML.

Paid font distributor: [fonts.com](https://www.fonts.com/) - download the font and include it in our website directory and then link to it using `@font-face` ruleset.

<br>

### Web Fonts using `<link>`

1. Select the font in Google Fonts
2. Choose the styles available for your font
3. Copy the automatically generated `<link>` element
4. Paste it in the `<head>` tag (before our CSS `<link>`).
5. Use the font

<br>

### Web Fonts using `@font-face`

Fonts can be downloaded just like any other file on the web.

They come in a few different file formats, such as:

- OTF (OpenType Font)
- TTF (TrueType Font)
- WOFF (Web Open Font Format)
- WOFF2 (Web Open Font Format 2)

The different formats are a progression of standards for how fonts will work with different browsers, with WOFF2 being the most progressive. It’s a good idea to include TTF, WOFF, and WOFF2 formats with your `@font-face` rule to ensure compatibility on all browsers.

How to use `@font-face`:

1. On the same page from Google Fonts, click Download to download the font files to our computer. The file will be downloaded as a single format `TTF`. We can use a tool [google-webfonts-helper](https://gwfh.mranftl.com/fonts) to generate additional file types for `WOFF` and `WOFF2`.
2. Add the downloaded files to our website's directory.
3. Use the font using `@font-face` at the top of our CSS file:

```
@font-face {
  font-family: 'Roboto Font';
  src:
    url("fonts/Roboto.woff2") format("woff2"),
    url("fonts/Roboto.woff") format("woff"),
    url("fonts/Roboto.ttf") format("truetype");
}
```

4. Within `@font-face`, with `font-family` we set a custom name for the downloaded font, surrounded by quotation marks.
5. The `src` property contains three values, each specifying the relative path to the font file and its format.
6. Note that the ordering for the different formats is important because our browser will start from the top of the list and search until it finds a font format that it supports.

Once the `@font-face` is defined, you can use the font in your stylesheet with the given custom name.

```css
h1 {
  font-family: "Roboto Font";
}
```

<br>

-->
