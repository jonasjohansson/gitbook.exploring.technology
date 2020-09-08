# Transparent Video

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

