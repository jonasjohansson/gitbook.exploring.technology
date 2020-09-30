# Barcode

Made up of simple patterns, barcodes come in several configurations and are easy to use. Run the [barcode generator](https://au.gmented.com/app/marker/marker.php) to see what they look like, and read about the quality of the [different markers](https://github.com/nicolocarpignoli/artoolkit-barcode-markers-collection). 

To use it in code, update the marker `value` number and set the same `matrixCodeType` as used in the generators. The once available are:

* AR\_MATRIX\_CODE\_3x3
* AR\_MATRIX\_CODE\_3x3\_HAMMING63
* AR\_MATRIX\_CODE\_3x3\_PARITY65
* AR\_MATRIX\_CODE\_4x4
* AR\_MATRIX\_CODE\_4x4\_BCH\_13\_9\_3
* AR\_MATRIX\_CODE\_4x4\_BCH\_13\_5\_5

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

![Barcode 0](../../../../.gitbook/assets/0000.png)

![Barcode 1](../../../../.gitbook/assets/0001.png)



![Barcode 3](../../../../.gitbook/assets/0002%20%281%29.png)

