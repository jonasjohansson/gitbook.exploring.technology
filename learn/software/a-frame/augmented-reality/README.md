# Augmented Reality

For many years great augmented reality has been only available for native apps and special mobile devices, but it's now possible to use directly in the browser!

The best way to understand more is to create a site using the code below \(or [visit this example in your phone](https://codepen.io/nicolocarpignoli/full/vMBgob)\) and look at the marker.

{% tabs %}
{% tab title="Code" %}
```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@1.0.1/dist/aframe-master.min.js"></script>
    <script src="https://rawgit.com/jeromeetienne/AR.js/master/aframe/build/aframe-ar.min.js"></script>
  </head>
  <body>
    <a-scene >
      <a-marker preset="hiro">
        <a-box color="red"></a-box>
      </a-marker>
      <a-entity camera></a-entity>
    </a-scene>
  </body>
</html>

```
{% endtab %}

{% tab title="Marker" %}
![](../../../../.gitbook/assets/hiroqr.png)
{% endtab %}
{% endtabs %}

The augmented reality super powers are made possible by including [AR.js](https://github.com/jeromeetienne/AR.js/) as a script tag in the `<head>` and adding "artoolkit" to `<a-scene>`. The regular camera is replaced with the &lt;a-marker-camera&gt; which supports presets and custom markers, and more:

| Attribute | Description | Options |
| :--- | :--- | :--- |
| type | type of marker | pattern, barcode, unknown |
| size | size of the marker in meter |  |
| url | url of the pattern **if** type is pattern |  |
| value | value of the barcode **if** type is barcode |  |
| preset | parameters preset | hiro, kanji |
| emitevents | emits 'markerFound' and 'markerLost' | true, false |
| smooth | turn on/off camera smoothing | true, false |
| smoothCount | number of matrices to smooth tracking over, more = smoother but slower follow - default: 5 |  |
| smoothTolerance | distance tolerance for smoothing, if smoothThreshold \# of matrices are under tolerance, tracking will stay still - default: 0.01 |  |
| smoothThreshold | threshold for smoothing, will keep still unless enough matrices are over tolerance - default: 2 |  |

{% hint style="success" %}
Hide the VR button by including `vr-mode-ui="enabled: false`" in `<a-sce`
{% endhint %}

{% embed url="https://vimeo.com/373737450" %}

