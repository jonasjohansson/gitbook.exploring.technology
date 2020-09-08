# 7. Media

Both video and audio can be added directly to entities, turning them into live screens or speakers.

{% page-ref page="video/" %}

{% page-ref page="sound.md" %}

Both are fun to add, but they often come with playback issues, especially on mobile devices.

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

This script will automatically play all media files as soon as the window is clicked or touched. It's a good place to start.

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

