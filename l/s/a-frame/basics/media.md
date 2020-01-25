# Media

Attaching external media can have a great impact, especially when using audio. To avoid having the media play when loaded \(which is often the case with large media files\) use the built-in asset manager! It will create a [loading screen](https://github.com/aframevr/aframe/blob/master/docs/components/loading-screen.md) that comes with some default styling which can be changed.

```markup
<a-scene loading-screen="dotsColor: red; backgroundColor: black; enabled: true"></a-scene>
```

To add assets add either an `<audio>` or `<video>` element in `<a-assets>` and then reference the element in the scene, with `<a-sound>` for audio and `<a-video>` for video. To ignore the asset manager, simply add the sound link directly to the `src` attribute. 

{% tabs %}
{% tab title="Audio" %}
```markup
<a-assets>
  <audio
    id="noise"
    src="https://cdn.aframe.io/basic-guide/audio/backgroundnoise.wav"
    autoplay
    loop
    preload
    crossorigin="anonymous"
  ></audio>
</a-assets>
<a-sound src="#noise"></a-sound>
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

{% hint style="danger" %}
Remove the **autoplay** and **muted** for the video to not be muted or play automatically from the start.
{% endhint %}

For 360 video, use `<a-videosphere>` which will wrap a video around a sphere, perfect for 360 content.

```markup
<a-videosphere src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4"></a-videosphere>
```

### Troubleshooting

#### Audio or Video does not work on mobile

Due to privacy settings audio or video does not autoplay on mobile devices, instead they must be triggered by a user action.  However, it is possible to circumvent this by adding a custom script in `<head>`.

```markup
<script>
  window.addEventListener("click", function() {
    for (el of document.querySelectorAll("audio,video")) {
      el.play();
    }
  });
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

