# Webcam texture

```markup
<html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <script src="https://aframe.io/releases/0.9.2/aframe.min.js"></script>
  </head>
  <body>
    <a-scene>
      <a-assets>
        <video id="webcam" playsinline></video>
      </a-assets>

      <a-videosphere
        position="-1 0.5 -3"
        rotation="0 45 0"
        shadow
        material="src: #webcam"
      ></a-videosphere>
    </a-scene>

    <script>
      // You can also set which camera to use (front/back/etc)
      // @SEE https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia
      navigator.mediaDevices
        .getUserMedia({ audio: false, video: true })
        .then(stream => {
          let $video = document.querySelector("video");
          $video.srcObject = stream;
          $video.onloadedmetadata = () => {
            $video.play();
          };
        });
    </script>
  </body>
</html>

```

