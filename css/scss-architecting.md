[&larr; back](./README.md)

# Architecting: Organizing Files

**The 7-1 Pattern** - create **7 folders** for partial Sass files, and 1 main Sass file where we will import all of our partial files, and then compile everything in one final CSS style sheet. Not mandatory to use all of these folders, it depends on the project's size and scope.

Create a `sass/` folder containing the following 7 folders:

- `base/` - basic product definitions
- `components/` - one file for each component
- `layout/` - where we define the overall layout of the project
- `pages/` - styles for specific pages, e.g. `_home.scss`
- `abstracts/` - code that doesn’t output any CSS, such as variables and mixins
- `themes/` - if you want to implement different visual themes
- `vendors/` - for third party CSS

<br>

## 7-1 pattern in details

- **`main.scss`** - file that serves for imports

<br>

- **`base/`** - for basic definitions.

  - `_base.scss` low level basics, such as resets and styles for the `html` and `body` elements.
  - `_animations.scss` file for `@keyframe` animations.
  - `_typography.scss` all the styles related to typograph.
  - `_utilities.scss` for CSS utility classes

<br>

- **`abstracts/`** - for code that will not output any CSS, e.g. variables, mixins, etc.

  - `_variables.scss`
  - `_mixins.scss`
  - `_functions.scss`

<br>

- **`components/`** - here we create one file for each particular component.

  - `_button.scss`

<br>

- **`layout/`** - a file for each piece of global layout of the entire project, e.g. global header, global footer.

  - Layout elements that work everywhere on all pages.
  - `_header.scss`
  - `_footer.scss`

<br>

- **`pages/`** - specific styles for a specific page, like the homepage.

  - `_home.scss`

<br>

Our Sass files are partials, that's why we name them with an underscore.

<br>

## Guidance

**base/ abstracts/ components/ layouts/ pages/** - these are the most important folders.

- **themes/** - for web apps with different themes
- **vendors/** - for third party CSS, like bootstrap, or an icon system, or an animation framework.

The **components** are the building blocks which are independent and reusable everywhere across our website, and the **layout** is what holds all of these components together.

This architecture is designed to handle complex projects (useful for maintaining the code over time). For simple landing pages we should use something simpler.

<br>

## Another Sass files structure

_For small projects:_

```
sass/
	_base.scss
	_features.scss
	_footer.scss
	_gallery.scss
	_header.scss
	_homes.scss
	_realtors.scss
	_sidebar.scss
	_story.scss
	_typography.scss
	main.scss
```

<br>
