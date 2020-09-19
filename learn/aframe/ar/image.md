# Image

It is possible to use complex images as markers, thanks to Natural Feature Tracking \(NFT\). For NFT to work, the system has to be trained with a surface in advance to recognise and track the surface. The training can be done using the [NFT Marker Creator](https://github.com/Carnaux/NFT-Marker-Creator) \(recommended\) or the[ online  version](https://carnaux.github.io/NFT-Marker-Creator-Web/) \(very slow, max width and height less than 1000px\). 

In order to create good markers, [read this guide](https://github.com/Carnaux/NFT-Marker-Creator/wiki/Creating-good-markers), and follow the [NFT Image Constraints](https://github.com/kalwalt/jsartoolkit5/blob/fixing-nft/doc/NFT_image_constraints.md) \(rectangular, JPEG\).

{% hint style="danger" %}
Image tracking demands more computing power and will behave very slow on older devices.
{% endhint %}

The marker creator will give a confidence score, and it's also possible to use  [Vuforia's Target Manager](https://developer.vuforia.com/) \(developer account is free\) and proceed based on the result. **Have at least 3 stars.**

![This image has lots of unique features!](../../../.gitbook/assets/vuforia%20%283%29.jpg)

For reference on ideal data, this [Augmented Reality Marker Generator](http://www.brosvision.com/ar-marker-generator/) creates images that are ideal for tracking.

Once generated the three files \(fset, fset3, iset\) should be placed together in relation to the code below. If the name of the file was **pinball** then **PATH\_TO\_FILE** should be the same.

```markup
<html>
	<head>
		<script src="https://unpkg.com/aframe@latest"></script>
		<script src="https://raw.githack.com/AR-js-org/AR.js/master/aframe/build/aframe-ar-nft.js"></script>
	</head>
	<body>
		<a-scene renderer="logarithmicDepthBuffer: true;" embedded arjs>
			<a-nft type="nft" url="PATH_TO_FILE" smooth="true" smoothCount="10" smoothTolerance=".01" smoothThreshold="5">
				<a-box color="red" scale="10 10 10"></a-box>
			</a-nft>
			<a-entity camera></a-entity>
		</a-scene>
	</body>
</html>
```

{% hint style="info" %}
Is your app slow? Read [10 tips to enhance your AR.js app](https://medium.com/chialab-open-source/10-tips-to-enhance-your-ar-js-app-8b44c6faffca) by for tips on performance.
{% endhint %}

