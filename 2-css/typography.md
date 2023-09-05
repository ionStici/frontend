[&larr; Back](./README.md)

# Typography

## font-family

Property that changes the typeface of the text.

```css
h1 {
  font-family: "Times New Roman", serif;
}
```

- Accepts a comma-separated list of strings representing font families
- For multiple words typefaces, use quotation marks `""`
- Use similar _[Web safe fonts](https://www.cssfontstack.com/)_ for fallbacks in case the font is not available
- Above `serif` is the fallback. A group of similar looking fonts: _a font stack_

<br>

Font properties are inherited. So, declare your font styles on a parent container like `body`

- **`font-size`** change the size of text elements. Accepts: keywords, length units and percentages
- **`font-weight`** set the boldness of text. Numeric values: `100` to `900`
- **`font-style`** set whether a font should be styled with a `normal`, `italic`, or `oblique` face

<div></div>

- **`line-height`** space between text lines (unitless values)
- **`letter-spacing`** horizontal space between characters (length values)
- **`word-spacing`** space between words in a text (length values)

<div></div>

- **`{ font: 400 16px / 1.5 oblique serif }`** shorthand property.

<div></div>

- **`text-transform`** transform text to `uppercase`, `lowercase` or `capitalize`
- [**`text-decoration`**](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration) shorthand property sets the appearance of decorative lines on text

<div></div>

- **`text-indent`** add indent to blocks of text (length values)

- `text-align` align text to its parent element.

<br>

## Vertical Align

```css
span {
  vertical-align: top;
}
```

Sets vertical alignment of an inline, inline-block or table-cell text.

Check [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/vertical-align) for more options.

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
