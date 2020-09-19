# Model Viewer

Browsers can present 3D models using the [Model Viewer](https://modelviewer.dev/) component. No interaction available besides control of camera, but enables the model to be viewed in the browser as well as in VR and AR!

```markup
<html>
  <head>
    <script
      type="module"
      src="https://unpkg.com/@google/model-viewer/dist/model-viewer.js"
    ></script>
    <style>
      body {
        margin: 0;
      }
      model-viewer {
        width: 100%;
        height: 100%;
      }
    </style>
  </head>
  <body>
    <model-viewer
      src="https://modelviewer.dev/shared-assets/models/Astronaut.glb"
      ar
      ar-modes="webxr scene-viewer quick-look fallback"
      ar-scale="auto"
      camera-controls
      skybox-image="https://modelviewer.dev/shared-assets/environments/aircraft_workshop_01_1k.hdr"
      ios-src="https://modelviewer.dev/shared-assets/models/Astronaut.usdz"
    ></model-viewer>
  </body>
</html>
```



