[&larr; Back](./README.md)

# Visual Studio Code

[**Visua Studio Code**](https://code.visualstudio.com/)

<br>

<!-- - Emmet / Prettier / ES Lint / tool-specific extensions / etc. -->

### VS Code Settings (suggestions)

- _Format On Save:_ **ON**
- _Auto Save:_ **onFocusChange**
- _Word Wrap:_ **OFF**
- _File Icon Theme:_ **Seti** (Visual Studio Code)
- _Tab Size:_ **4** (prettier have default indentation)
- _Detect Indentation:_ **OFF** (to don't override "Tab Size")

<div></div>

- Connect VS Code with your GitHub account to sync your settings.

### VS Code Theme (suggestion)

- One Monokai

### VS Code Extensions (basic)

- **Auto Close Tag** - to automatically close HTML tags. [Link→](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag)
- **Auto Rename Tag** - to automatically update matching HTML tags. [Link→](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)
- **Color Highlight** - to highlight colors in CSS code. [Link→](https://marketplace.visualstudio.com/items?itemName=naumovs.color-highlight)

<div></div>

- **Image Preview** - to display an image preview next to the code. [Link→](https://marketplace.visualstudio.com/items?itemName=kisstkondoros.vscode-gutter-preview)
- **Paste and Indent** - to automatically indent pasted code. [Link→](https://marketplace.visualstudio.com/items?itemName=Rubymaniac.vscode-paste-and-indent)
- **Path Intellisense** - to autocomplete filenames. [Link→](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)

<div></div>

- **Prettier** - to automatically format code. [Link→](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- **Live Server** - to create a live preview for the current project. [Link→](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

<br>

## Snippets in VS Code

Snippets insert boiler code based on some short identifier.

**Path:** Code -> Settings -> Configure User Snippets -> New Global Snippets file..

Then, insert the name of your new snippet, e.g. `cl`, in turn we get a file named `cl.code-snippets`

Modify the `prefix` and `body` properties with the snippet you need.

```js
{
  "Print to console": {
    "scope": "javascript,typescript",
    "prefix": "cl",
    "body": ["console.log($1);"],
  }
}
```

Now, when you type `cl`, you can press enter and you get the code from the `body` property.

<br>
