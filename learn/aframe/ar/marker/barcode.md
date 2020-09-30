# Barcode

Made up of simple patterns, barcodes come in several configurations and are easy to use. Run the [barcode generator](https://au.gmented.com/app/marker/marker.php) to see what they look like, and read about the quality of the [different markers](https://github.com/nicolocarpignoli/artoolkit-barcode-markers-collection). 

![](../../../../.gitbook/assets/marker-generator%20%281%29.png)

{% hint style="info" %}
Notice that the marker image resolution is set to 300 dpi, the barcode dimensions are 4x4 and the correction type is 13,5,5. Identical as what is used in the code below.
{% endhint %}

To use it, update the marker `value` number and set the same `matrixCodeType` as used in the generator. The once available are:

* 3x3
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
		<a-scene embedded arjs="detectionMode: mono_and_matrix; matrixCodeType: 4x4_BCH_13_5_5;">
			<a-marker type="barcode" smooth="true" value="0">
        <a-box color="red"></a-box>
      </a-marker>
      <a-marker type="barcode" smooth="true" value="1">
        <a-box color="green"></a-box>
      </a-marker>
      <a-marker type="barcode" smooth="true" value="2">
        <a-box color="blue"></a-box>
      </a-marker>
			<a-entity camera></a-entity>
		</a-scene>
	</body>
</html>
```



![Barcode 0, 1, 2](../../../../.gitbook/assets/barcodes%20%281%29.jpg)

