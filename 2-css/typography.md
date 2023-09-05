[&larr; Back](./README.md)

# Typography

Properties related to font are usually inherited. We use the font properties on the parent or root element (like `body` or `html`) and in the end all the siblings inherit them.

<br>

## Table of Content

- [font-family](#font-family)
- [Font Size](#font-size)
- [font-weight](#font-weight)
- [font-style](#font-style)
- [font](#font)
- [text-transform](#text-transform)
- [Text Layout Properties](#text-layout-properties)
- [Text Decoration](#text-decoration)
- [Vertical Align](#vertical-align)
- [Web Fonts](#web-fonts)
  - [Web Fonts using `<link>`](#web-fonts-using-link)
  - [Web Fonts using `@font-face`](#web-fonts-using-font-face)

<br>

## font-family

Property that changes the typeface of the text.

```css
h1 {
  font-family: "Times New Roman", serif;
}
```

- `font-family` accepts a comma-separated list of strings representing font families
- For multiple words typefaces, use quotation marks `""`
- Use similar _[Web safe fonts](https://www.cssfontstack.com/)_ for fallbacks in case the font is not available
- Above `serif` is the fallback. A group of similar looking fonts: _a font stack_

<br>

## Font Size

```css
p {
  font-size: 16px;
}
```

<br>

## font-weight

How bold or think the text appears. Accepts keywords or numerical values.

```css
h1 {
  font-weight: 400;
}
```

Keywords: `bold`, `normal`, `lighter`, `bolder`

Numerical values can range from `1` (lightest) to `1000` (boldest).

- `400` is equal to the keyword value `normal`
- `700` equal to `bold`. There is also `lighter` and `bolder`

_Note:_ not all font weights work for all fonts. Look up the font you are using to see which font-weight values are available.

<br>

## font-style

```css
h1 {
  font-style: italic;
}
```

Values: `normal`, `italic`, `oblique`

<br>

## Font

```css
p {
  font: 400 16px / 1.5 italic serif;
}
```

`font` is a shorthand property.

`font-family` and `font-size` and mandatory to add, the rest are all optional.

`line-height` must come after font-size separated by slash ( / ).

<br>

## text-transform

```css
h1 {
  text-transform: uppercase;
}
```

Transform text to `uppercase`, `lowercase` or `capitalize`.

<br>

## Text Layout Properties

```css
h1 {
  letter-spacing: 1px;
  word-spacing: 2px;
  line-height: 1.5;
  text-align: center; /* left right center justify */
  text-indent: 25px;
}
```

- `letter-spacing: units` horizontal space between letters.
- `word-spacing: units` space between words.
- `line-height` space between text lines. Unitless values are recommended as they will respond to the current font size.
- `text-align` align text to its parent element.
- `text-indent` indentation

<br>

## Text Decoration

```css
p {
  text-decoration: none; /* no styles */
}
```

[text-decoration](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration) shorthand property sets the appearance of decorative lines on text.

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
