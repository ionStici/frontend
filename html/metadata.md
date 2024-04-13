# Metadata

Two types of meta tags: (1) **`http-equiv`** praga directives, (2) **`name`** named meta types

Both must include the `content` attribute which defines the content for the type of metadata listed.

## Description

`description` is what search engines display under the page's title in seach results (Important for SEO).

```html
<meta name="description" content="Quality web development services" />
```

The description should be a short and accurate summary of the page's content.

## Author

Define the author of the page (who wrote the page).

```html
<meta name="author" content="John" />
```

## Robots

By default, search engines will index the site.

```html
<meta name="robots" content="noindex, nofollow" />
```

This meta tag tells the seach engine bots to not index the site and not follow any links.

## Theme color

`theme-color` define a color to customize the browser interface. This will provide a suggested color for the user agents that support coloring the title bar, tab bar, or other chrome components.

```html
<meta name="theme-color" content="#226DAA" />
```

## Open Graph

Open graph meta tags: Generate a link preview card for the document. Facebook media card:

```HTML
<meta property="og:title" content="Page title" />
<meta property="og:description" content="Page description" />
<meta property="og:image" content="./image.jpg" />
<meta property="og:image:alt" content="Alt description for the img above" />
```

Twitter has its own [Twitter Cards](https://developer.twitter.com/en/docs/twitter-for-websites/cards/overview/markup) syntax.

If not included, social media sites will correctly grab the title of your page and the description from the description meta tag, the same information as search engines will present, but you can intentionally set what you want users to see when a link is posted to your site.
