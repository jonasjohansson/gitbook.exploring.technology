# Video

Entities can use videos as sources, the same way as images. Use the built-in asset manager to ensure all media has been loaded before the site is visible. 

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

{% hint style="warning" %}
I have found better performance using &lt;a-asset-item&gt; especially when adding video.
{% endhint %}

