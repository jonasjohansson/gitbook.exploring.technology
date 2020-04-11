# 1. Scene

Include the A-Frame library as a `<script>` in  `<head>` and add the `<a-scene>` in  `<body>`. To remove the VR icon visible in the bottom right we tell `<a-scene>` to hide it using `vr-mode-ui` attribute .

{% embed url="https://jsfiddle.net/jonasjohansson/dyf0sLbx/3/" %}



```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
  </head>
  <body>
    <a-scene vr-mode-ui="enabled: false">
    </a-scene>
  </body>
</html>
```

