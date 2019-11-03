# Audio

Audio is important for providing immersion and presence in VR. Even adding simple white noise in the background goes a long way. We recommend having some audio for every scene. One way would be to add an `<audio>` element to to our HTML \(preferably under `<a-assets>`\) to play an audio file:

```markup
<a-scene>
  <a-assets>
    <audio src="https://cdn.aframe.io/basic-guide/audio/backgroundnoise.wav" autoplay
      autoplay loop preload crossorigin="anonymous"></audio>
  </a-assets>
</a-scene>
```

{% hint style="danger" %}
The `crossorigin="anonymous"` is  important to add!
{% endhint %}

Or we can add positional audio using `<a-sound>`. This makes the sound get louder as we approach it and get softer as we distance from it. We could place the sound in our scene using `position`.

```markup
<a-scene>
  <a-sound src="https://cdn.aframe.io/basic-guide/audio/backgroundnoise.wav" autoplay="true"
    position="-3 1 -4"></a-sound>
</a-scene>
```

### Audio does not work on mobile when running AR

Due to privacy settings audio does not autoplay on mobile devices, instead they must be triggered by a user action. However, it is possible to circumvent this by adding a custom script in `<head>`.

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

And then you can add a special entity containing your marker entity file.

```markup
<a-marker marker-sound-toggle>
</a-marker>
```

Whenever the marker is now detected the content should play, and pause when detection is lost.

