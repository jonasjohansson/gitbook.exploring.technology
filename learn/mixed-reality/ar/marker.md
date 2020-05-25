# Marker

[Markers](https://ar-js-org.github.io/AR.js-Docs/marker-based/) are black and white and used with the `<a-marker>` entity. Create a site using the code below \(or [visit this example in your phone](https://codepen.io/nicolocarpignoli/full/vMBgob)\) and look at the marker to better understand its usage.

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
![](../../../.gitbook/assets/hiroqr.png)
{% endtab %}
{% endtabs %}

In case the preset default marker is not special enough it's possible to design your own! The custom design should:

* Be square
* JPEG
* Include no transparency
* Preferably be black and white \(strive for contrast\)
* Have at least 10% distance to the edges
* Not be mirrored ie. no identical sides

Once the image is made:

1. Visit the [Marker Generator](https://ar-js-org.github.io/AR.js/three.js/examples/marker-training/examples/generator.html)
2. Upload the image
3. Download the Marker pattern file and the Marker image
4. Upload the pattern file and reference it in the code.

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

It is possible to have a higher ratio than the default 0.5, but by doing so it's also imperative to tell A-Frame that the new marker has changed. By adding the **patternRatio** to the **arjs** attribute of `<a-scene>` this can be accomplished!

```markup
<a-scene embedded arjs="patternRatio: 0.7">
```

