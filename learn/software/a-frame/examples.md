# Examples

## [https://github.com/nicolocarpignoli](https://github.com/nicolocarpignoli)

## Augmented Reality Video

```markup
<html>
  <head>
    <script src="https://aframe.io/releases/0.9.2/aframe.min.js"></script>
    <script src="https://rawgit.com/jeromeetienne/AR.js/master/aframe/build/aframe-ar.min.js"></script>
    <script>
      AFRAME.registerComponent("marker-video-toggle", {
        init: function() {
          var marker = this.el;
          let video = document.querySelector("video");
          marker.addEventListener("markerFound", function() {
            video.play();
          });
          marker.addEventListener("markerLost", function() {
            video.pause();
          });
        }
      });
    </script>
  </head>
  <body>
    <a-scene
      embedded
      arjs
    >
      <video
        id="video"
        crossorigin="anonymous"
        autoplay
        loop
        muted
        src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
      ></video>
      <a-marker type="pattern" preset="hiro" marker-video-toggle>>
          <a-video rotation="-90 0 0" src="#video"></a-video>
      </a-marker>
      <a-entity camera></a-entity>
    </a-scene>
  </body>
</html>

```

## 

![Ash Tree \(2019\)](https://cdn.glitch.com/9fefbf1d-1435-435b-a215-8f0dd88f40eb%2Fpattern-tree.png?v=1570454328480)



![Virtual Dancer \(2018\)](https://lh6.googleusercontent.com/acLEkmbGahFpGv6_UYAU9EaVqyuDzalq-4awSSQBdtnBlDDwE_LFe1TsJjDAzEO6GDqIt9O-m8RbQTTI1BMuOj_L_2XpDFAKqxmZOXC2Ddim5tVj7wytiuu42GvGqSuuZ4ZPWg2R5Uk)



