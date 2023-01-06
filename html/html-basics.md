# **HTML**

**HTML** stands for _HyperText Markup Language_, and it is the code that structure the webpage.

- A _markup_ language is a computer language that defines the structure and presentation of raw text.
- _HyperText_ is text displayed on a computer that provides access to other text through links.

<br>

## **Table of Content**

- [HTML Elements Anatomy]()
- [Anatomy of an HTML document]()

<br>

## **HTML Elements Anatomy**

HTML is composed of elements, example:

```HTML
<p> Hello </p>  // a html element
```

A HTML element is composed of:

- An opening tag `<p>`
- The content `Hello`
- A closing tag `<p>`

The purpose of HTML elements is to define the content and structure of the webpage.

There are many tags that we can use to organize and display text and other types of content, like images.

<br>

## **Anatomy of an HTML document**

HTML is organized as a collection of family tree relationships.

We can _nest_ elements by placing an element within other elements.

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>Document</title>
    </head>
    <body>
        <h1>Hello World</h1>
        <p>This whole structure is a html document</p>
    </body>
</html>
```

- `body` Only content inside this element can be displayed to the screen.

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

# **Attributes**

<br>

## **Table of Content**

- [Custom Link Preview](#custom-link-preview)
- [`download`](#download)
- [`contenteditable`](#contenteditable)
- [`autocomplete`](#autocomplete)
- [`spellcheck`](#spellcheck)
- [`readonly`](#readonly)

<br>

### **Custom Link Preview**

```HTML
<meta property="og:title" content="Page title" />
<meta property="og:description" content="Page description" />
<meta property="og:image" content="./image.jpg" />
```

Generate link preview for your webpage with this meta tags.

<br>

### `download`

```HTML
<a href="/file.jpg" download>Download File</a>
```

Specifies that the target file (specified in href) will be downloaded when user clicks on the hyperlink.

<br>

### `contenteditable`

```HTML
<p contenteditable="true">Editable</p>
```

Specifies whether the content of an element is editable or not.

<br>

### `autocomplete`

```HTML
<input type="text" autocomplete="off" />
```

`autocomplete` allows the browser to predict the value.

<br>

### `spellcheck`

```HTML
<input type="text" spellcheck="true" />
```

Checks the spelling.

<br>

### `readonly`

```HTML
<input type="text" readonly />
```

The field is read-only and can not be edited.
