[&larr; Back](./README.md)

# Audio and Video

- `<video>` and `<audio>` elements, along with the `src` attribute, are used to embed media players.
- Or can be used as the container element for a series of `<source>` elements, each providing a `src` file suggestion.
- Fallback content is included between the opening and closing tags for situations when the user agent doesn't support `<video>` or `<audio>`.

<br>

## Table of Content

- [Audio](#audio)
- [Video](#video)
- [Video and Sources](#video-and-sources)

<br>

## Audio

`<audio>` is used to embed audio content into a document.

```html
<audio controls>
  <source src="hello.mp3" type="audio/mp3" />
</audio>
```

`controls` attribute automatically displays the audio controls into the browser such as play and mute.

<br>

## Video

```html
<video src="video.mp4" width="320" height="240" controls>
  <p>Video not supported</p>
</video>
```

The video source can be a video file from our directory, or a URL that points to a video file hosted on internet.

The `<p>` element will only be displayed if the browser is unable to load the video.

- `controls` add video controls.
- `autoplay` the video automatically playing as soon as the page is loaded.
- `mute` the video is paused.
- `loop` the video continuously playing on repeat
- `poster` attribute provides an image to display while the video is downloading.

Note: `<embed>` tab used to incorporate media content into a page, but it is deprecated.

<br>

## Video and Sources

```html
<video poster="./img.jpg" width="320" height="240" controls>
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

- About [tracks](https://web.dev/learn/html/audio-video/#tracks)

- About [custom media controls](https://web.dev/learn/html/audio-video/#custom-media-controls)

<br>
