# Barcode

Made up of very simple patterns, barcodes come in many configurations and are easy to use. Run the [generator](https://au.gmented.com/app/marker/marker.php) to see what they look like!

```markup
<html>
	<head>
		<script src="https://unpkg.com/aframe@latest"></script>
		<script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>
	</head>
	<body>
		<a-scene embedded arjs="detectionMode: mono_and_matrix; matrixCodeType: 4x4_BCH_13_5_5;">
			<a-marker type="barcode" smooth="true" value="0">
    		<a-box color="red"></a-box>
			</a-marker>
			<a-entity camera></a-entity>
		</a-scene>
	</body>
</html>
```

![](../../../../.gitbook/assets/00.png)

