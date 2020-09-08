# 7. Video

Entities can use videos as sources, the same way as images. Use the built-in asset manager to ensure all media has been loaded before the site is visible. The manager will present a [loading screen](https://github.com/aframevr/aframe/blob/master/docs/components/loading-screen.md) that comes with some editable styling.

```markup
<a-scene loading-screen="dotsColor: red; backgroundColor: black;"></a-scene>
```

To add assets add a `<video>` element in `<a-assets>` and then reference the element in the scene using `<a-video>`. To ignore the asset manager, simply add the video directly to the `src` attribute.

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

{% hint style="info" %}
Pay attention to the attributes **autoplay**, **loop** and **muted** and remove then if necessary.
{% endhint %}

For 360 video, use `<a-videosphere>` which will wrap a video around a sphere, perfect for 360 content.

```markup
<a-videosphere src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4"></a-videosphere>
```

It's possible to upload assets and reference them, and to get started even faster, visit [Wikimedia Commons](https://commons.wikimedia.org/wiki/Main_Page) where there is a large database of open media!

### Video does not play

Due to privacy settings media with sound does not autoplay and must be triggered by a user action. However, it is possible to circumvent this by adding a custom script in `<head>`.

```markup
<script>
	const play = () => {
		window.removeEventListener('touchstart', play)
		document.querySelectorAll('video').forEach(el => el.play())
	}
	window.addEventListener('touchstart', play)
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

