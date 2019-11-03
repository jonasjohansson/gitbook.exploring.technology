# Stereo Viewing

{% embed url="https://github.com/oscarmarinmiro/aframe-stereo-component" %}

```markup
<!DOCTYPE html>
<html>
<head>
	<script src="https://unpkg.com/aframe@0.8.2/dist/aframe-master.js"></script>
	<script src="https://rawgit.com/jeromeetienne/AR.js/master/aframe/build/aframe-ar.min.js"></script>
	<script src="https://unpkg.com/aframe-extras@4.1.2/dist/aframe-extras.loaders.min.js"></script>
	<script src="https://unpkg.com/three@0.95.0/examples/js/libs/inflate.min.js"></script>
  <script src="https://unpkg.com/aframe-stereo-component@0.6.0/dist/aframe-stereo-component.min.js"></script>
</head>
<body>
	<a-scene>
    <a-box color="red" position="0 0 -1"></a-box>
    <a-camera position="-1 0 10" cursor-visible="false" stereocam="eye:left;"></a-camera>
    <a-camera position="1 0 10" cursor-visible="false" stereocam="eye:right;"></a-camera>
    
	</a-scene>
  
</body>
</html>
```

