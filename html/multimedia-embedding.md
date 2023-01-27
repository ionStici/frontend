# Multimedia and Embedding

<br>

## Videos

Add videos to the webpage.

```html
<video src="video.mp4" width="320" height="240" controls autoplay loop>
  Video not supported
</video>
```

The video source can be a video file from our webpage, or a URL that points to a video file hosted on another webpage.

The text `Video not supported` will only be displayed if the browser is unable to load the video.

- `controls` add video controls.
- `autoplay` the video automatically playing as soon as the page is loaded.
- `loop` the video continuously playing on repeat

Note: `<embed>` tab used to incorporate media content into a page, but it is deprecated.

<br>

## Audio

`<audio>` is used to embed audio content into a document.

```html
<audio autoplay controls>
  <source src="audio-file.mp3" type="audio/mp3" />
</audio>
```

`controls` attribute automatically displays the audio controls into the browser such as play and mute.
