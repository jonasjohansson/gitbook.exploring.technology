# 8. Sound



Adding media can have a great impact, especially when using audio. To avoid having the media play only when loaded use the built-in asset manager. It will create a [loading screen](https://github.com/aframevr/aframe/blob/master/docs/components/loading-screen.md) that comes with some default styling which can be changed.

```markup
<a-scene loading-screen="dotsColor: red; backgroundColor: black;"></a-scene>
```

To add assets add an `<audio>` or `<video>` element in `<a-assets>` and then reference the element in the scene, with `<a-entity sound="">` for audio and `<a-video>` for video. To ignore the asset manager, simply add the sound link directly to the `src` attribute.

{% tabs %}
{% tab title="Audio" %}
```markup
<a-assets>
  <audio
    id="guitar"
    src="https://upload.wikimedia.org/wikipedia/commons/d/d1/Little_guitar_%28Antti_Luode%29.mp3"
    preload="auto"
    crossorigin="anonymous"
  ></audio>
</a-assets>
<a-entity sound="src: #guitar;" geometry="primitive: plane" material="color: blue"></a-entity>
```
{% endtab %}

{% tab title="Video" %}
```markup
<a-assets>
  <video
    id="bunny"
    src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
    autoplay
    loop
    preload
    muted
    crossorigin="anonymous"
  ></video>
</a-assets>
<a-video src="#bunny" position="0 0 -3"></a-video>
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Pay attention to the attributes **autoplay**, **loop** and **muted** and remove then if necessary.
{% endhint %}

For 360 video, use `<a-videosphere>` which will wrap a video around a sphere, perfect for 360 content.

```markup
<a-videosphere src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4"></a-videosphere>
```

It's possible to upload assets and reference them, and to get started even faster, visit [Wikimedia Commons](https://commons.wikimedia.org/wiki/Main_Page) where there is a large database of open media!

### Media does not play

Due to privacy settings audio or video with audio does not autoplay and must be triggered by a user action.  However, it is possible to circumvent this by adding a custom script in `<head>`.

```markup
<script>
  const play = () => {
    window.removeEventListener("touchstart", play);
    window.removeEventListener("click", play);
    document.querySelectorAll("video").forEach(el => el.play());
    document
      .querySelectorAll("[sound],a-sound")
      .forEach(el => el.components.sound.playSound());
  };
  window.addEventListener("touchstart", play);
  window.addEventListener("click", play);
</script>
```

If using AR it is possible to use a marker being found as a trigger.

{% tabs %}
{% tab title="Audio" %}
```markup
<script>
  AFRAME.registerComponent('marker-audio-toggle', {
    init: function () {
      var marker = this.el;
      let audio = document.querySelector('audio');
      marker.addEventListener('markerFound', function() {
        audio.play();
      });
      marker.addEventListener('markerLost', function() {
        audio.pause();
      });
    }
  });
</script>
```
{% endtab %}

{% tab title="Video" %}
```markup
<script>
  AFRAME.registerComponent('marker-video-toggle', {
    init: function () {
      var marker = this.el;
      let video = document.querySelector('video');
      marker.addEventListener('markerFound', function() {
        video.play();
      });
      marker.addEventListener('markerLost', function() {
        video.pause();
      });
    }
  });
</script>
```
{% endtab %}

{% tab title="Legacy" %}
```markup
<script>
  AFRAME.registerComponent('marker-sound-toggle', {
    init: function () {
      var marker = this.el;
      let sound = marker.querySelector('[sound]');
      marker.addEventListener('markerFound', function() {
        sound.components.sound.playSound();
      });
      marker.addEventListener('markerLost', function() {
        sound.components.sound.pauseSound();
      });
    }
  });
</script>
```
{% endtab %}
{% endtabs %}

And then you can add a special entity to the `<a-marker>`.

```markup
<a-marker marker-video-toggle>
  <a-video src="#video"></a-video>
</a-marker>
```

### Webcam texture

```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
  </head>
  <body>
    <a-scene>
      <a-assets>
        <video id="webcam"></video>
      </a-assets>
      <a-videosphere material="src: #webcam"></a-videosphere>
    </a-scene>
    <script>
      // You can also set which camera to use (front/back/etc)
      // @SEE https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia
      navigator.mediaDevices
        .getUserMedia({ audio: false, video: true })
        .then(stream => {
          let video = document.querySelector("video");
          video.srcObject = stream;
          video.onloadedmetadata = () => {
            video.play();
          };
        });
    </script>
  </body>
</html>
```

