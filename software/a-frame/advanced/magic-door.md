# Magic door

What's this? It's a custom effect made to create the illusion that something is coming out of the marker. A bit hard to imagine? Check out this video:

{% embed url="https://www.youtube.com/watch?v=371ZQW\_Yzck" %}

What's happening here is that there's actually invisible walls placed around the content which blocks the scene behind, making it appear as if it's only visible "through the door". As the user walks closer, and steps inside, the walls disappear, and suddenly you are in that world. Very cool!

First we have to add a custom component which, when applied, will occlude everything _behind_ it.

```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@0.9.2/dist/aframe-master.js"></script>
    <script src="https://rawgit.com/jeromeetienne/AR.js/master/aframe/build/aframe-ar.min.js"></script>
    <script>
      AFRAME.registerComponent("occlude", {
        init: function() {
          var el = this.el;
          var mesh = el.getObject3D("mesh");
          var material = new THREE.MeshBasicMaterial({
            colorWrite: false
          });
          mesh.material = material;
        }
      });
      AFRAME.registerComponent("marker-video-toggle", {
        init: function() {
          var marker = this.el;
          let video = document.querySelector('video');
          marker.addEventListener('markerFound', function() {
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
    <a-scene embedded arjs="debugUIEnabled: false">
      <video
        id="video"
        crossorigin="anonymous"
        autoplay
        loop
        muted
        src="https://cdn.glitch.com/82c2a70f-78fb-4e66-b933-a2efafbb5617%2Faframe-city-360.mp4?v=1569784310782"
      ></video>
      <a-marker type="pattern" preset="hiro" marker-video-toggle>
        <a-ring
          rotation="-90 0 0"
          radius-inner="1.2"
          radius-outer="4"
          occlude
        ></a-ring>
        <a-ring
          rotation="-90 0 0"
          radius-inner="1"
          radius-outer="1.2"
          color="black"
        ></a-ring>
        <a-sphere
          radius="1"
          phi-length="-180"
          theta-length="180"
          rotation="-90 0 0"
          src="#video"
        >
        </a-sphere>
      </a-marker>
      <a-entity camera></a-entity>
    </a-scene>
  </body>
</html>
```

As you can see this code uses a custom component which, when applied, will occlude everything _behind_ it. And when the marker is detected we are showing a half-sphere with a vide attached to it, and a ring-object obscuring the edges.

### Create a Frame

```markup
<a-entity id="frame" scale="0.5 1 0.5" position="0 0.1 0">
  <a-plane
    rotation="-90 0 0"
    position="3 0 0"
    scale="4 4 1"
    occlude
  ></a-plane>
  <a-plane
    rotation="-90 0 0"
    position="-3 0 0"
    scale="4 4 1"
    occlude
  ></a-plane>
  <a-plane
    rotation="-90 -90 0"
    position="-0.5 0 -3"
    scale="4 4 1"
    occlude
  ></a-plane>
  <a-plane
    rotation="-90 -90 0"
    position="-0.5 0 3"
    scale="4 4 1"
    occlude
  ></a-plane>
</a-entity>
```

