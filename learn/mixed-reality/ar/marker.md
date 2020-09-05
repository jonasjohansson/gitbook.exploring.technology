# Marker

[Markers](https://ar-js-org.github.io/AR.js-Docs/marker-based/) are black and white and use the `<a-marker>` entity. Adapt the code below, visit the site on your mobile device and look at [this Hiro marker](https://raw.githubusercontent.com/stemkoski/VR-AR-class-examples/master/markers/hiro.png).  You should see a red box. Reload if it doesn't work the first time.

```markup
<html>
	<head>
		<script src="https://unpkg.com/aframe@latest"></script>
		<script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>
	</head>
	<body style="margin: 0; overflow: hidden">
		<a-scene embedded arjs>
			<a-marker preset="hiro" smooth="true">
				<a-box color="red"></a-box>
			</a-marker>
			<a-entity camera></a-entity>
		</a-scene>
	</body>
</html>
```

### Custom marker

In case the preset is not special enough, it's possible to design your own. For great detection the marker should:

* Be rotationally asymmetrical \(be different from all rotations\)
* Include no transparency \(export as JPEG\)
* Preferably use only black and white \(look for contrast\)
* Have at least 10% distance to the edges

Once the image is made:

1. Visit the [Marker Generator](https://ar-js-org.github.io/AR.js/three.js/examples/marker-training/examples/generator.html)
2. Upload the image
3. Download the **Marker pattern** and the **Marker image**
4. Upload and reference the pattern file

```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
    <script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>
  </head>
  <body>
    <a-scene embedded arjs="debugUIEnabled: false">
      <a-marker type="pattern" url="YOUR_MARKER_PATH.patt">
        <a-box color="red"></a-box>
      </a-marker>
      <a-entity camera></a-entity>
    </a-scene>
  </body>
</html>
```

### Changing the Pattern Ratio

It is possible to have a higher ratio than the default 0.5, but by doing so it's also imperative to include this information. By adding the **patternRatio** to the **arjs** attribute of `<a-scene>` this can be accomplished.

```markup
<a-scene embedded arjs="patternRatio: 0.7;">
```

### Improving performance

While not heavily tested, it might be possible to gain an increase in performance by adding `renderer="logarithmicDepthBuffer: true;"` to  `<a-scene>`.

