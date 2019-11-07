---
description: 'https://jeromeetienne.github.io/AR.js/three.js/examples/arcode.html'
---

# Augmented Reality

For many years great augmented reality has been only available for native apps and special mobile devices, but it's now possible to use directly in the browser! The simplest way to understand more is to create a site using the code below and [view the Hiro marker](https://raw.githubusercontent.com/jeromeetienne/AR.js/master/three.js/examples/marker-training/examples/pattern-images/pattern-hiro.png).

You can also [create your own AR code with a QR code embedded](%20https://jeromeetienne.github.io/AR.js/three.js/examples/arcode.html).

```markup
<html>
<head>
	<script src="https://unpkg.com/aframe@0.9.2/dist/aframe-master.js"></script>
	<script src="https://rawgit.com/jeromeetienne/AR.js/master/aframe/build/aframe-ar.min.js"></script>
</head>
<body>
	<a-scene embedded arjs="debugUIEnabled: false">
		<a-marker type="pattern" preset="hiro">
		    <a-box color="red"></a-box>
		</a-marker>		
		<a-entity camera></a-entity>
	</a-scene>
</body>
</html>
```

![](https://raw.githubusercontent.com/jeromeetienne/AR.js/master/three.js/examples/marker-training/examples/pattern-images/pattern-hiro.png)

