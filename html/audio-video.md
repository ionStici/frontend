## Audio and Video

- `<video>` and `<audio>` elements, along with the `src` attribute, are used to embed media players.
- Or can be used as the container element for a series of `<source>` elements, each providing a `src` file suggestion.
- Fallback content is included between the opening and closing tags (in case the user agent doesn't support `<video>` or `<audio>`).

Attributes: `controls autoplay loop mute preload`

Video only attributes: `height width poster`

- `poster` provides an image to display while the video is downloading.
- `controls` provides user video controls.

_Video example using multiple sources:_

```html
<video poster="./img.jpg">
  <source src="media.webm" type="video/webm" />
  <source src="media.mp4" type="video/mp4" />
  <source src="media.ogv" type="video/ogg" />
  <p>Watch <a href="youtube.com/link">video on YouTube</a></p>
</video>
```

`<video>` serves as the container for multiple `<source>` elements.

Each `<source>` contains a `src` and `type` attribute.

The `type` attribute informs the browser of the linked file's media type. This prevents the browser from fetching media files it wouldn't be able to decode.

Within the `type` attribute, we can include a [codecs](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/codecs_parameter) parameter, which specifies exactly how the resource is encoded.

Make sure to define the aspect ratio of your video, because when the video loads, a size difference between the poster and the video will cause a reflow and repaint.

If you want a background video, consider the following: purely decorative, ARIA role of none, omit any fallback content, no tracks, include `autoplay` `loop` `muted` attributes.

About [tracks](https://web.dev/learn/html/audio-video/#tracks)

About [Custom media controls](https://web.dev/learn/html/audio-video/#custom-media-controls)
