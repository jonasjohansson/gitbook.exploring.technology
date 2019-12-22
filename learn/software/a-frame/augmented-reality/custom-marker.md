# Custom Marker

In case the preset default marker is not special enough it's possible to design your own! The custom design should:

* be square
* exported as JPEG
* include no transparency
* preferably be black and white \(strive for contrast\)
* have at least 10% distance to the edges
* not be mirrored ie. no sides identical

Once the image is made:

1. Visit the [Marker Generato](https://jeromeetienne.github.io/AR.js/three.js/examples/marker-training/examples/generator.html)r
2. Upload the image
3. Download the Marker pattern file and the Marker image
4. Upload the pattern file to Glitch and reference it in the code.

```markup
<html>
<head>
	<script src="https://unpkg.com/aframe@0.9.2/dist/aframe-master.js"></script>
	<script src="https://rawgit.com/jeromeetienne/AR.js/master/aframe/build/aframe-ar.min.js"></script>
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

It is possible to have a higher ratio than the default 0.5, but by doing so it's also imperative to tell A-Frame that the new marker has changed. By adding the _patternRatio_ to the _arjs_ attribute of `<a-scene>` this can be accomplished!

```markup
<a-scene embedded arjs="patternRatio: 0.7">
```

