[&larr; Back](./README.md)

# Text Elements

## Basics

- Six **heading** levels, from `<h1>` (most important) to `<h6>` (least important).
- `<p>` (paragraph) contains a block of plain text.
- `<span>` used to separate small pieces of content (no semantic).

<br>

## Text elements

- `<code>` documenting code examples (displayed in monospace font).
- `<pre>` renders text exactly as written in the source code.
- `<data>` links a given piece of content with a machine-readable translation using `value` attribute.
- `<time>` for time text. `datetime` attribute can transate dates into machine-readable format (better SEO).
- `<samp>` for sample output from a computer program.
- `<kbd>` mimics text as keyboard input.
- `<var>` can be used for math expressions or programming variables.
- `<sup>` superscript and `<sub>` subscript.
- `<del>` to indicate text that has been removed (optionally including `cite` and `datetime`).
- `<s>` renders text with a line through it (for text that is no longer relevant).
- `<ins>` used to indicate text that has been added (apposite of `<del>`).
- `<abbr>` represents an abbreviation or acronym. Use `title` attribute if the expansion is not present.
- `<dfn>` for identifying a term that is being defined within its surrounding content.
- `<blockquote>` for marking up quotations. Include a `cite` attribute with the url quote source.
- `<q>` for inline quotations.
- Use the `lang` attribute to identify the language of a specific area of content.

<br>

## Emphasizing text

Elements used to emphasize text based on a semantic reason:

- `<em>` to emphasize or stress a span of content.
- `<mark>` to highlight text that is somehow relevant.
- `<strong>` identifies text as having strong importance.
- `<cite>` used to mark the titles of books, articles, or other creative work.

<div></div>

Little to no semantic value:

- `<i>` can be used for technical terms, foreigh words, thoughts, or ship names.
- `<u>` is for content that has non-textual annotation.
- `<b>` can be used to draw attention to text that is not otherwise important (no semantic).

<br>
