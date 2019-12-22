# Custom Marker NFT

It is recently possible to use imagery as a marker, thanks to Natural Feature Tracking \(NFT\). For NFT to work, the system has to be trained with a surface in advance to recognise and track the surface. The training can be done using the [NFT Marker Creator](https://github.com/Carnaux/NFT-Marker-Creator) \(recommended\) or the[ online  version](https://carnaux.github.io/NFT-Marker-Creator-Web/) \(max width and height less than 1000px\). The image should also follow the [NFT Image Constraints](https://github.com/kalwalt/jsartoolkit5/blob/fixing-nft/doc/NFT_image_constraints.md) \(rectangular, JPEG\).

{% hint style="danger" %}
Make sure the file extension is visible, or the marker creator may not run the file.
{% endhint %}

_Insert example for A-Frame and custom NFT marker here._

To test whether the image is a great candidate for AR, upload it to [Vuforia's Target Manager](https://developer.vuforia.com/) \(developer account is free\) and proceed based on the result.

![This image has lots of unique features!](../../../../.gitbook/assets/vuforia%20%283%29.jpg)

For reference on ideal data, this [Augmented Reality Marker Generator](http://www.brosvision.com/ar-marker-generator/) creates images that are ideal for tracking.

