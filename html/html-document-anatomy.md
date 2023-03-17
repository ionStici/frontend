[&larr; Back](./README.md)

# Anatomy of an HTML document

```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <title>HTML Document</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  </head>
  <body>
    <h1>Hello World</h1>
  </body>
</html>
```

1. `<!DOCTYPE html>` Document type declaration, it acts as an instruction for the browser, should be the first line of code in html.
   Tells the browser what type of document to expect and what version of HTML is being used in the document.

2. `<html>` tags, the root element, wrapps all the content, anything between these tags will be interpreted as HTML code.

3. `<html lang="en-US" >` the `lang` attribute defines the main language of the document. The value of the `lang` attribute is a two or three-letter ISO language code followed by the region. The region is optional. The `lang` attribute can be use in other HTML tags that differ from the main document language.

4. `<head>` tag contains the metadata (information) about the web page. It isn't displayed directly on the web page, it can appear in search results, other roles.

5. `<meta charset="utf-8" />` meta element (should be the first tag). It sets the character set for your document to UTF-8, which includes most characters from the vast majority of human written languages. With this setting, the page can now handle any textual content.

6. `<title>` title of the page (appears in the browser tab, when it is bookmarked, search results).

7. `viewport` meta tag. Makes the site responsive, by making the width of the content the width of the screen. Check the documentation for more.

8. `<body>` element, it contains all the content displayed on the page.

<br>

## The Link element

The `link` element is used to create relationships between the HTML document and external resources. The type of relationship is defined by the value of the `rel` attribute. There are currently 25 available values for the `rel` attribute.

<br>

## Link CSS and JS

```html
<head>
  <link rel="stylesheet" href="./style.css" />
  <script src="./script.js" defer></script>
</head>
```

<br>

## Favicon

Define a favicon for your document. There are lots of other icon types to consider.

```html
<head>
  <link rel="icon" href="/ico.png" type="image/png" sizes="16x16 32x32 48x48" />
</head>
```

<br>

## Alternate and Canonical

- `rel="alternate"` to identify translations, or alternate representations of the site.
- When using `alternate` for a translation, the `hreflang` attribute must be set.

```html
<head>
  <link rel="alternate" href="https://my-site.com/fr/" hreflang="fr-FR" />
  <link rel="alternate" href="https://my-site.com/pt/" hreflang="pt-BR" />
  <link rel="canonical" href="https://my-site.com" />
</head>
```

In case we have several translations of our website, we should use `rel="canonical"` to avoid confusion with search engines. `canonical` will identify the preferred URL for the site. Indicate the preferred URL using this tag on all the translated pages and on the home page as well.

<br>

<!-- [`<base />`](https://web.dev/learn/html/document-structure/#base) -->
