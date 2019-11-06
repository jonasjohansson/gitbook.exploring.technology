# HTML

An additional way of handling text, or any kind of content, is to use a shader that turns HTML into canvas, ready to be used as a texture.

```
<html>
  <head>
    <script src="https://aframe.io/releases/0.9.2/aframe.min.js"></script>
    <script src="https://unpkg.com/aframe-html-shader@0.2.0/dist/aframe-html-shader.min.js"></script>
    <style>
      #targetHTML {
        width: 100%;
        height: 100%;
        position: fixed;
        left: 0;
        top: 0;
        z-index: 11;
        overflow: hidden;
        font-size: 96px;
        background-color: yellow;
        color: green;
        text-align: center;
      }
      #targetHTML div {
        position: relative;
        top: 50%;
        transform: translateY(-50%);
      }
    </style>
  </head>
  <body>
    <a-scene background="color: blue">
      <a-entity
        geometry="primitive: box"
        material="shader: html; target: #targetHTML; ratio: width"
      ></a-entity>
      <a-entity camera position="0 0 3"></a-entity>
    </a-scene>
    <div id="targetHTML">
      <div>Hello, HTML!</div>
    </div>
  </body>
</html>
<head> </head>

```

