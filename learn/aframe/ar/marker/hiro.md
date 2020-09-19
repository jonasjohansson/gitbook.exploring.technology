# Hiro

The most basic test pattern. To try it, add the code below, and visit the URL on your phone ****\([remember to type "https://" before the URL](../../../../tools/glitch.md#force-https)\). Accept camera permissions and look at the marker. If successful you should see a red box appear where the marker is.

```markup
<html>
	<head>
		<script src="https://unpkg.com/aframe@latest"></script>
		<script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>
	</head>
	<body>
		<a-scene embedded arjs>
			<a-marker preset="hiro" smooth="true">
				<a-box color="red"></a-box>
			</a-marker>
			<a-entity camera></a-entity>
		</a-scene>
	</body>
</html>
```

![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LFNtKzfzIWfc8anmKip%2F-MGTzViYNlUj-js9IS_4%2F-MGUZXkpAF6U_q1mp3KD%2Fhiro.jpg?alt=media&token=5f5a7d2c-8d96-46f2-b8a3-4a839e0fb8d4)

