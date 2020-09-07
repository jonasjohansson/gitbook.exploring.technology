# 1. Scene

Include the A-Frame library as a `<script>` in  `<head>` and add the `<a-scene>` in  `<body>`. 

```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
  </head>
  <body>
    <a-scene background="color: #eee">
    </a-scene>
  </body>
</html>
```

{% hint style="info" %}
To remove the VR icon in the bottom right we tell `<a-scene>` to hide it using `vr-mode-ui` attribute.
{% endhint %}

