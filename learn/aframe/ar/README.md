# Augmented Reality

For a long time, great augmented reality has been only available for native apps and special mobile devices, but it's now possible to use directly in the browser! The best way to understand more, is to create a site using the code below \(or [visit this example in your phone](https://codepen.io/nicolocarpignoli/full/vMBgob)\) and look at the marker.

{% tabs %}
{% tab title="Code" %}
```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
    <script src="https://rawgit.com/jeromeetienne/AR.js/master/aframe/build/aframe-ar.min.js"></script>
  </head>
  <body>
    <a-scene vr-mode-ui="enabled: false;"
      renderer="logarithmicDepthBuffer: true;"
      embedded
      arjs="trackingMethod: best; sourceType: webcam;debugUIEnabled: false;">
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
![](../../../.gitbook/assets/hiroqr.png)
{% endtab %}
{% endtabs %}

The augmented reality super powers are made possible by including [AR.js](https://github.com/jeromeetienne/AR.js/) as a script tag in the `<head>`. The entity `<a-marker>` come with several settings that help define the type of markers to look for, and how to behave when found, and it is inside of this tag that the visible content is placed.

| Attribute | Description | Options | Default |
| :--- | :--- | :--- | :--- |
| type | type of marker | pattern, barcode, unknown |  |
| size | size of the marker in meter |  |  |
| url | url of the pattern **if** type is pattern |  |  |
| value | value of the barcode **if** type is barcode |  |  |
| preset | parameters preset | hiro, kanji |  |
| emitevents | emits 'markerFound' and 'markerLost' | true, false | false |
| smooth | turn on/off camera smoothing | true, false | false |
| smoothCount | number of matrices to smooth tracking over, more = smoother but slower follow |  | 5 |
| smoothTolerance | distance tolerance for smoothing, if smoothThreshold \# of matrices are under tolerance, tracking will stay still |  | 0.01 |
| smoothThreshold | threshold for smoothing, will keep still unless enough matrices are over tolerance |  | 2 |

{% hint style="success" %}
Hide the VR button by including `vr-mode-ui="enabled: false`" in `<a-sce`
{% endhint %}

{% embed url="https://vimeo.com/373737450" %}

