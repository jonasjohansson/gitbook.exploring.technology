# Video

You know already that the src of an entity can be both an image and a video, but you could also use the `<a-video>` entity, let's try it!

```
<a-scene>
  <a-video src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"></a-video>
</a-scene>
```

Or we can add an `<a-videosphere>` which will wrap a video around a sphere, perfect for 360 content.

```
<a-scene>
  <a-videosphere src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4"></a-videosphere>
</a-scene>
```

### Video without sound does not work on mobile

Due to privacy settings media does not autoplay on mobile devices, instead they must be triggered by a user action. However, it is possible to circumvent this by adding a custom script in `<head>`.

```
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

You must also add the video separately and reference it using the **id** and **src** attribute:

```
<video id="video" crossorigin="anonymous" autoplay loop muted src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"></video>
```

And then you can add a special entity to the `<a-marker>`.

```
<a-marker marker-video-toggle>
  <a-video src="#video"></a-video>
</a-marker>
```

Whenever the marker is now detected the content should play, and pause when detection is lost.

### Video with sound does not work on mobile

If your video has sound there has to be an explicit user interaction, instead of the above add the following script _after_ the `<a-scene>` element. This is also dependant on you referencing all videos using the `<video>` tag.

```
<script>
  var videos = document.querySelectorAll("video");
  window.addEventListener("click", function() {
    for (video of videos) {
      video.play();
    }
  });
</script>
```

{% hint style="danger" %}
Remove the **autoplay** and **muted** for the video to not be muted or play automatically from the start.
{% endhint %}

