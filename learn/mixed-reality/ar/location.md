# Location

To add entities relative to the world use [GPS coordinates](https://www.gps-coordinates.net/) and the **gps-entity-place** attribute.Read [this guide](https://medium.com/chialab-open-source/build-your-location-based-augmented-reality-web-app-c2442e716564) to learn more, and [check out the official documentation](https://ar-js-org.github.io/AR.js-Docs/).

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
        look-at="[gps-camera]"
        gps-entity-place="latitude: 59.3462392062857; longitude: 18.149601701117785"
      ></a-box>
      <a-camera gps-camera rotation-reader></a-camera>
    </a-scene>
  </body>
</html>
```

