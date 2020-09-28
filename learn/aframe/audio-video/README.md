# 7. Audio & Video

Media such as audio and video can be added directly to entities, turning them into live screens or speakers. And by using the Asset Manager, these files can be preloaded so everything is ready when intended. Add `<a-assets>` immediately after the `<a-scene>` and start adding your files using the `<a-asset-item>` entity.

```markup
<a-assets>
  <a-asset-item id="YOUR_ID" src="YOUR_LINK"></a-asset-item>
  <a-asset-item id="YOUR_ID2" src="YOUR_LINK2"></a-asset-item>
</a-assets>
<a-entity sound="src: #YOUR_ID;"></a-entity>
<a-video src="#YOUR_ID2"></a-video>
```

The manager will present a [loading screen](https://github.com/aframevr/aframe/blob/master/docs/components/loading-screen.md) that comes with some editable styling.

```markup
<a-scene loading-screen="dotsColor: red; backgroundColor: black;"></a-scene>
```

Both audio and video are fun to add, but they often come with playback issues, especially on mobile devices.

Due to privacy settings media with sound does not autoplay and must be triggered by a user action. However, it is possible to circumvent this by adding a custom script in `<head>`.

```markup
<script>
  const play = () => {
    window.removeEventListener("click", play);
    window.removeEventListener("touchstart", play);
    window.removeEventListener("click", play);
    document.querySelectorAll("video").forEach(el => el.play());
    document
      .querySelectorAll("[sound],a-sound")
      .forEach(el => el.components.sound.playSound());
  };
  window.addEventListener("click", play);
  window.addEventListener("touchstart", play);
</script>
```

This script will automatically play all media files as soon as the window is clicked or touched. It's a good place to start. If using AR it is possible to use a marker being found as a trigger.

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

