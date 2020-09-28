# 6. Media

## Video

Entities can use videos as sources, the same way as images. Use the built-in asset manager to ensure all media has been loaded before the site is visible. To add assets add a `<video>` element in `<a-assets>` and then reference the element in the scene using `<a-video>`.

```markup
<a-assets>
  <a-asset-item
    id="sample"
    src="https://file-examples-com.github.io/uploads/2017/04/file_example_MP4_480_1_5MG.mp4"
    autoplay
    loop
    muted
    preload
  ></a-asset-item>
</a-assets>
<a-video src="#sample" position="0 0 -4"></a-video>
```

{% hint style="info" %}
Pay attention to the attributes **autoplay**, **loop** and **muted** and remove then if necessary.
{% endhint %}

## Videosphere

For 360 video, use `<a-videosphere>` which will wrap a video around a sphere, perfect for 360 content.

```markup
<a-videosphere src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4"></a-videosphere>
```

## Audio

Entities can also have sounds attached, creating positional audio objects as well as normal background tracks. To add assets add an `<audio>` or `<a-asset-item>` element in `<a-assets>` and then reference the element in the scene, with `<a-entity sound="">`.

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

## Media doesn't play

Due to privacy settings media with sound does not autoplay and must be triggered by a user action. Add the following script in `<head>`.

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

