# Marker

[Markers](https://ar-js-org.github.io/AR.js-Docs/marker-based/) can be of three types: **Hiro**, **Barcode** and **Pattern**. To try it out, add the code below, and visit the URL on your phone ****\(remember to use https\). Accept camera permissions and look at [this Hiro marker](https://raw.githubusercontent.com/stemkoski/VR-AR-class-examples/master/markers/hiro.png). If successful you should see a red box appear where the marker is. Besides swift testing, the Hiro marker is not very useful.

{% tabs %}
{% tab title="Code" %}
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
{% endtab %}

{% tab title="Marker" %}
![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LFNtKzfzIWfc8anmKip%2F-MGTzViYNlUj-js9IS_4%2F-MGUZXkpAF6U_q1mp3KD%2Fhiro.jpg?alt=media&token=5f5a7d2c-8d96-46f2-b8a3-4a839e0fb8d4)
{% endtab %}
{% endtabs %}

## Barcode

Made up of very simple patterns, barcodes come in many configurations and are easy to use. Run the [Barcode generator](https://au.gmented.com/app/marker/marker.php) to see what they look like!

{% tabs %}
{% tab title="Code" %}
```markup
<a-marker type="barcode" value="0">
    <a-box color="red"></a-box>
</a-marker>
```
{% endtab %}

{% tab title="Marker" %}
![](../../../../.gitbook/assets/00.png)
{% endtab %}
{% endtabs %}

## Pattern

In case the previous types is not custom enough, it's possible to design your own. There's a few resources to get started like this [Figma template](https://www.figma.com/file/uZVaf3zJOGiZOpAIsOA3pT/WebAR-Pattern-Creator), [Stemkoski's](https://github.com/stemkoski) basic markers \(grab both [pattern](https://github.com/stemkoski/AR.js-examples/tree/master/data) and [image](https://github.com/stemkoski/AR.js-examples/tree/master/markers)\), the [Aruco generator](https://chev.me/arucogen/) and the [barcode generator](https://www.cognex.com/resources/interactive-tools/free-barcode-generator).

Whichever you choose, make sure the image has the following qualities:

* Rotationally asymmetrical \(be different from all rotations\)
* No transparency \(export as JPEG\)
* Uses only black and white, or color with great contrast
* Has at least 10% distance to the edges

Once you have your image:

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
    <a-scene embedded arjs>
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

## Improving performance

While not heavily tested, it might be possible to gain an increase in performance by adding `renderer="logarithmicDepthBuffer: true;"` to  `<a-scene>`.

