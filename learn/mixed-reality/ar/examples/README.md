# Examples

## [Virtual Dancer](https://jonasjohansson.github.io/virtualdancer/ar/)

![](../../../../.gitbook/assets/armarker%20%281%29.jpg)

## [Ash' Tree](https://aframe-ash-tree.glitch.me/)

{% tabs %}
{% tab title="Marker" %}
![](https://cdn.glitch.com/9fefbf1d-1435-435b-a215-8f0dd88f40eb%2Fpattern-tree.png?v=1570454328480)
{% endtab %}

{% tab title="Code" %}
```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@0.9.2/dist/aframe-master.js"></script>
    <script src="https://rawgit.com/jeromeetienne/AR.js/master/aframe/build/aframe-ar.min.js"></script>
    <script src="https://unpkg.com/aframe-extras@4.1.2/dist/aframe-extras.loaders.min.js"></script>
    <script src="https://unpkg.com/three@0.95.0/examples/js/libs/inflate.min.js"></script>
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
    </script>
  </head>
  <body style="margin:0;">
    <a-scene
      embedded
      arjs="debugUIEnabled: false; trackingMethod: best; patternRatio: 0.7"
      vr-mode-ui="enabled: false"
    >
      <a-marker
        type="pattern"
        url="https://cdn.glitch.com/9fefbf1d-1435-435b-a215-8f0dd88f40eb%2Fpattern-tree.patt?v=1570454328148"
      >
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
        <a-sphere
          radius="1"
          phi-length="-180"
          theta-length="180"
          rotation="-90 0 0"
          position="0 0 0"
          src="https://cdn.glitch.com/9fefbf1d-1435-435b-a215-8f0dd88f40eb%2Fbg.jpg?v=1570460254232"
        >
        </a-sphere>
        <a-entity
          scale="0.001 0.001 0.001"
          rotation="-90 0 0"
          position="0 0 0"
          fbx-model="src: url(https://cdn.glitch.com/9fefbf1d-1435-435b-a215-8f0dd88f40eb%2Ftree.fbx?v=1570456580699);"
        ></a-entity>
      </a-marker>
      <a-entity camera></a-entity>
    </a-scene>
  </body>
</html>

```
{% endtab %}
{% endtabs %}

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



![Virtual Dancer \(2018\)](https://lh6.googleusercontent.com/acLEkmbGahFpGv6_UYAU9EaVqyuDzalq-4awSSQBdtnBlDDwE_LFe1TsJjDAzEO6GDqIt9O-m8RbQTTI1BMuOj_L_2XpDFAKqxmZOXC2Ddim5tVj7wytiuu42GvGqSuuZ4ZPWg2R5Uk)



