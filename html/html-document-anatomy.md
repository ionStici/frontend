[&larr; Back](./README.md)

# Anatomy of an HTML document

```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <title>HTML Document</title>
  </head>
  <body>
    <h1>Hello World</h1>
  </body>
</html>
```

1. `<!DOCTYPE html>` Document type declaration, it acts as an instruction for the browser, should be the first line of code in html.
   Tells the browser what type of document to expect and what version of HTML is being used in the document.

2. `<html>` tags, the root element, wrapps all the content, anything between these tags will be interpreted as HTML code.

3. `<head>` tag contains the metadata (information) about the web page.
   It isn't displayed directly on the web page, it can appear in search results, other roles.

4. `<meta charset="utf-8" />` meta element. It sets the character set for your document to UTF-8, which includes most characters from the vast majority of human written languages. With this setting, the page can now handle any textual content.

5. `<title>` title of the page (appears in the browser tab, and when it is bookmarked).

6. `<body>` element, it contains all the content displayed on the page.

<br>
