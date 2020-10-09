# Magic door

The magic door effect is made to create the illusion of a room, which can only be seen through a door \(or portal\). Difficult to imagine? [Check out this video](https://youtu.be/371ZQW_Yzck).

What's happening here is that there are invisible walls placed around the content which occludes the scene behind.

{% tabs %}
{% tab title="Component" %}
```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
    <script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>
    <script src="aframe-frame.js"></script>
  </head>
  <body>
    <a-scene embedded arjs>
      <a-assets>
        <image
          id="wood"
          src="https://images.unsplash.com/photo-1561458338-60c444223320?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=975&q=80"
        ></image>
        <image
          id="sky"
          src="https://images.unsplash.com/photo-1537210249814-b9a10a161ae4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2089&q=80"
        ></image>
      </a-assets>
      <a-box id="frame" scale="0.05 0.05 0.1" src="#wood"></a-box>
      <a-marker preset="hiro" smooth="true">
        <a-entity>
          <a-entity frame="width: 1; height: 1; frameEl: #frame"></a-entity>
          <a-sphere
            scale="-1 1 1"
            rotation="90 -90 90"
            radius="6"
            phi-length="180"
            theta-length="180"
            src="#sky"
            material="side: back"
          ></a-sphere>
          <!--<a-sphere position="0 4 0" rotation="-180 90 90" phi-length="360"></a-sphere>-->
        </a-entity>
      </a-marker>
      <a-entity camera></a-entity>
    </a-scene>
  </body>
</html>
```
{% endtab %}

{% tab title="Frame" %}
```markup
<html>
	<head>
		<script src="https://unpkg.com/aframe@latest"></script>
		<script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>
		<script>
			AFRAME.registerComponent('occlude', {
				init: function () {
					var el = this.el
					var mesh = el.getObject3D('mesh')
					var material = new THREE.MeshBasicMaterial({
						colorWrite: false
					})
					mesh.material = material
				}
			})
			AFRAME.registerComponent('marker-video-toggle', {
				init: function () {
					var marker = this.el
					let video = document.querySelector('video')
					marker.addEventListener('markerFound', function () {
						video.play()
					})
					marker.addEventListener('markerLost', function () {
						video.pause()
					})
				}
			})
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
				<a-entity id="frame" scale="0.5 1 0.5" position="0 0.1 0">
					<a-plane rotation="-90 0 0" position="3 0 0" scale="4 4 1" occlude></a-plane>
					<a-plane rotation="-90 0 0" position="-3 0 0" scale="4 4 1" occlude></a-plane>
					<a-plane rotation="-90 -90 0" position="-0.5 0 -3" scale="4 4 1" occlude></a-plane>
					<a-plane rotation="-90 -90 0" position="-0.5 0 3" scale="4 4 1" occlude></a-plane>
				</a-entity>
				<!-- replace this with your content -->
				<a-sphere radius="1" phi-length="-180" theta-length="180" rotation="-90 0 0" src="#video"></a-sphere>
			</a-marker>
			<a-entity camera></a-entity>
		</a-scene>
	</body>
</html>
```
{% endtab %}

{% tab title="Ring" %}
```markup
<html>
	<head>
		<script src="https://unpkg.com/aframe@latest"></script>
		<script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>
		<script>
			AFRAME.registerComponent('occlude', {
				init: function () {
					var el = this.el
					var mesh = el.getObject3D('mesh')
					var material = new THREE.MeshBasicMaterial({
						colorWrite: false
					})
					mesh.material = material
				}
			})
			AFRAME.registerComponent('marker-video-toggle', {
				init: function () {
					var marker = this.el
					let video = document.querySelector('video')
					marker.addEventListener('markerFound', function () {
						video.play()
					})
					marker.addEventListener('markerLost', function () {
						video.pause()
					})
				}
			})
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
				<a-ring rotation="-90 0 0" radius-inner="1.2" radius-outer="4" occlude></a-ring>
				<a-ring rotation="-90 0 0" radius-inner="1" radius-outer="1.2" color="black"></a-ring>
				<!-- replace this with your content -->
				<a-sphere radius="1" phi-length="-180" theta-length="180" rotation="-90 0 0" src="#video"></a-sphere>
			</a-marker>
			<a-entity camera></a-entity>
		</a-scene>
	</body>
</html>
```
{% endtab %}
{% endtabs %}

