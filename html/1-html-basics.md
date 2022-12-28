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
