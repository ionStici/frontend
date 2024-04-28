# @supports

**Graceful degradation**

```css
div {
  background-color: rgba(0, 0, 0, 0.8);
}

@supports (-webkit-backdrop-filter: blur(10px)) or (backdrop-filter: blur(10px)) {
  .div {
    -webkit-backdrop-filter: blur(10px);
    backdrop-filter: blur(10px);
    background-color: rgba(0, 0, 0, 0.3);
  }
}
```

As parameters to `@supports` we pass the property that we want to test if the browser supports. And if it is supported, then the code block will wpply.
