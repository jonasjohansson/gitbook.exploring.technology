# Transparent Video

{% hint style="danger" %}
This does not work on Safari.
{% endhint %}

{% tabs %}
{% tab title="Transparent Video" %}
```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
    <script>
      AFRAME.registerComponent("transparent-video", {
        init: function() {
          this.el.addEventListener("materialtextureloaded", e => {
            let material = this.el.getObject3D("mesh").material;
            material.map.format = THREE.RGBAFormat;
            material.map.needsUpdate = true;
          });
        }
      });
    </script>
  </head>
  <body>
    <a-scene>
      <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
      <a-plane
        position="0 1 -2"
        material="src: https://simpl.info/videoalpha/video/dancer1.webm; transparent: true;"
        transparent-video
      ></a-plane>
    </a-scene>
  </body>
</html>
```
{% endtab %}

{% tab title="Transparent Video Shader \(doesn\'t work\)" %}
```markup
<html>
	<head>
		<script src="https://unpkg.com/aframe@latest"></script>
		<script src="https://unpkg.com/aframe-transparent-video-shader@1.0.1/dist/aframe-transparent-video-shader.umd.js"></script>
	</head>
	<body>
		<a-scene>
			<a-assets>
				<video id="videoId" src="https://simpl.info/videoalpha/video/dancer1.webm" muted autoplay loop></video>
			</a-assets>
			<a-entity
				material="shader: transparent-video; src: #videoId"
				geometry="primitive: plane;"
				position="0 0 -2"
			></a-entity>
		</a-scene>
	</body>
</html>
```
{% endtab %}
{% endtabs %}

