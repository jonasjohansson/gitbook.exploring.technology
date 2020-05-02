# Augmented Reality

AR in the browser is developing fast, thanks to efforts by the [AR.js](https://ar-js-org.github.io/AR.js-Docs/) team initiated by [Nicolò Carpignioli](https://twitter.com/nicolocarp). 

 The augmented reality super powers are made possible by including [AR.js](https://ar-js-org.github.io/AR.js-Docs/) in the `<head>`. There are currently three tracking methods available: **Marker**, **Location** and **Image**.

## Marker

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

You can also add a QR code so that it's not only a marker but it's also a link to the site. Generate a QR code that points to your website using [QR Code Generator](https://www.the-qrcode-generator.com/) or [QR Code Monkey](https://www.qrcode-monkey.com/).

1. Choose URL and add your website address
2. Choose Save and select SVG or PNG
3. Use the file in your image!

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

## Location

To add entities relative to the world use [GPS coordinates](https://www.gps-coordinates.net/). Add the attribute **gps-entity-place** to entities and provide latitude and longitude values. Read [this guide](https://medium.com/chialab-open-source/build-your-location-based-augmented-reality-web-app-c2442e716564) to learn more.

```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
    <script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar-nft.js"></script>
    <script src="https://unpkg.com/aframe-look-at-component@0.8.0/dist/aframe-look-at-component.min.js"></script>
  </head>
  <body>
    <a-scene gps-camera-debug embedded arjs>
      <a-box
        gps-entity-place="latitude: 59.3462392062857; longitude: 18.149601701117785"
      ></a-box>
      <a-camera gps-camera rotation-reader></a-camera>
    </a-scene>
  </body>
</html>
```

## Image

It is recently possible to use imagery as a marker, thanks to Natural Feature Tracking \(NFT\). For NFT to work, the system has to be trained with a surface in advance to recognise and track the surface. The training can be done using the [NFT Marker Creator](https://github.com/Carnaux/NFT-Marker-Creator) \(recommended\) or the[ online  version](https://carnaux.github.io/NFT-Marker-Creator-Web/) \(max width and height less than 1000px\). The image should also follow the [NFT Image Constraints](https://github.com/kalwalt/jsartoolkit5/blob/fixing-nft/doc/NFT_image_constraints.md) \(rectangular, JPEG\).

{% hint style="danger" %}
Make sure the file extension is visible, or the marker creator may not run the file.
{% endhint %}

_Insert example for A-Frame and custom NFT marker here._

To test whether the image is a great candidate for AR, upload it to [Vuforia's Target Manager](https://developer.vuforia.com/) \(developer account is free\) and proceed based on the result.

![This image has lots of unique features!](../../../.gitbook/assets/vuforia%20%283%29.jpg)

For reference on ideal data, this [Augmented Reality Marker Generator](http://www.brosvision.com/ar-marker-generator/) creates images that are ideal for tracking.

{% hint style="info" %}
Is your app slow? Read [10 tips to enhance your AR.js app](https://medium.com/chialab-open-source/10-tips-to-enhance-your-ar-js-app-8b44c6faffca) by for tips on performance.
{% endhint %}

