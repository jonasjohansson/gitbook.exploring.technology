# Magic door

The magic door effect is made to create the illusion of a room, which can only be seen through a door \(or portal\). Difficult to imagine? [Check out this video](https://youtu.be/371ZQW_Yzck).

What's happening here is that there are invisible walls placed around the content which occludes the scene behind. As the user walks closer, and steps inside, the walls disappear.

To accomplish this we have to add a custom component which, when applied, will occlude everything _behind_.

{% tabs %}
{% tab title="Component" %}
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
			AFRAME.registerComponent('frame', {
				schema: {
					size: { default: 3 }
				},
				init: function () {
					const self = this
					const SIZE = this.data.zize
					const HALF_PI = Math.PI / 2
			
					self.id = 'frame'
			
					for (let pos of ['top', 'bottom', 'left', 'right']) {
						let plane = document.createElement('a-plane')
						plane.id = pos
						plane.object3D.rotation.set(-HALF_PI, 0, 0)
						plane.setAttribute('occlude', true)
						switch (pos) {
							case 'top':
								plane.object3D.position.set(-SIZE, 0, 0)
								plane.object3D.scale.set(SIZE, SIZE, 1)
								break
							case 'bottom':
								plane.object3D.position.set(SIZE, 0, 0)
								plane.object3D.scale.set(SIZE, SIZE, 1)
								break
							case 'left':
								plane.object3D.position.set(0, 0, -SIZE)
								plane.object3D.scale.set(SIZE * 3, SIZE, 1)
								break
							case 'right':
								plane.object3D.position.set(0, 0, SIZE)
								plane.object3D.scale.set(SIZE * 3, SIZE, 1)
								break
						}
						self.update()
						self.el.appendChild(plane)
					}
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
				<a-entity frame></entity>
				<!-- replace this with your content -->
				<a-sphere radius="1" phi-length="-180" theta-length="180" rotation="-90 0 0" src="#video"></a-sphere>
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

