# Barcode

Made up of simple patterns, barcodes come in several configurations and are easy to use. Run the [barcode generator](https://au.gmented.com/app/marker/marker.php) to see what they look like, and read about the quality of the [different markers](https://github.com/nicolocarpignoli/artoolkit-barcode-markers-collection). 

To use it, update the marker `value` number and set the same `matrixCodeType` as used in the generator. The once available are:

* 3x3 \(**default**\)
* 3x3\_HAMMING63
* 3x3\_PARITY65
* 4x4
* 4x4\_BCH\_13\_9\_3
* 4x4\_BCH\_13\_5\_5

```markup
<html>
	<head>
		<script src="https://unpkg.com/aframe@latest"></script>
		<script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar.js"></script>
	</head>
	<body>
		<a-scene embedded arjs="detectionMode: mono_and_matrix">
			<a-marker type="barcode" smooth="true" value="0">
        <a-box color="red"></a-box>
      </a-marker>
      <a-marker type="barcode" smooth="true" value="10">
        <a-box color="green"></a-box>
      </a-marker>
      <a-marker type="barcode" smooth="true" value="20">
        <a-box color="blue"></a-box>
      </a-marker>
			<a-entity camera></a-entity>
		</a-scene>
	</body>
</html>
```

![MatrixCodeType 3x3: 0, 10, 20](../../../../.gitbook/assets/barcodes%20%282%29.jpg)

![MatrixCodeType 4x4: 0, 1, 2](../../../../.gitbook/assets/barcodes4x4.jpg)

