# Sound

Entities can also have sounds attached, creating positional audio objects as well as normal background tracks. Just like video, use the asset manager. 

To add assets add an `<audio>` element in `<a-assets>` and then reference the element in the scene, with `<a-entity sound="">`.

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

