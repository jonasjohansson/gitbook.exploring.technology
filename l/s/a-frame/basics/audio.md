# Audio

Audio is important for providing immersion and presence in VR. Even adding simple white noise in the background goes a long way. To accomplish this add an `<audio>` element to to our HTML \(preferably under `<a-assets>`\) to play an audio file.

```markup
<a-assets>
  <audio src="https://cdn.aframe.io/basic-guide/audio/backgroundnoise.wav" autoplay loop preload crossorigin="anonymous"></audio>
</a-assets>
```

{% hint style="danger" %}
The `crossorigin="anonymous"` is  important to add!
{% endhint %}

Or we can add positional audio using `<a-sound>`. This makes the sound get louder as we approach it and get softer as we distance from it. We could place the sound in our scene using `position`.

```markup
<a-sound src="https://cdn.aframe.io/basic-guide/audio/backgroundnoise.wav"></a-sound>
```

### Audio does not work on mobile when running AR

Due to privacy settings audio does not autoplay on mobile devices, instead they must be triggered by a user action. However, it is possible to circumvent this by adding a custom script in `<head>`.

{% tabs %}
{% tab title="Solution" %}
```markup
<script>
  window.addEventListener("click", function() {
    for (el of document.querySelectorAll("audio")) {
      el.play();
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

And then you can add a special entity containing your marker entity file.

```markup
<a-marker marker-sound-toggle>
    <a-sound src="https://cdn.aframe.io/basic-guide/audio/backgroundnoise.wav"></a-sound>
</a-marker>
```

Whenever the marker is now detected the content should play, and pause when detection is lost.
{% endtab %}
{% endtabs %}

