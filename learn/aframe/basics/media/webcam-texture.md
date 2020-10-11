# Webcam Texture

```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
  </head>
  <body>
    <a-scene>
      <a-assets>
        <video id="webcam"></video>
      </a-assets>
      <a-videosphere material="src: #webcam"></a-videosphere>
    </a-scene>
    <script>
      // You can also set which camera to use (front/back/etc)
      // @SEE https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia
      navigator.mediaDevices
        .getUserMedia({ audio: false, video: true })
        .then(stream => {
          let video = document.querySelector("video");
          video.srcObject = stream;
          video.onloadedmetadata = () => {
            video.play();
          };
        });
    </script>
  </body>
</html>
```

