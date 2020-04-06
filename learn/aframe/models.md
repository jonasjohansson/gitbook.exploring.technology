# 5. Models

Build you own using [Blender](https://www.blender.org/) and [Cinema4d](https://www.maxon.net/en-us/products/cinema-4d/overview/), or download models from [Thingiverse](http://thingiverse.com/), [Sketchfab](https://sketchfab.com/search?features=downloadable+animated&q=low+poly&sort_by=-pertinence&type=models) and [Poly](https://poly.google.com/). When downloaded, verify that the model looks OK by uploading it to [Creators 3d Online Viewer](https://www.creators3d.com/online-viewer).

In order to have models in your scene there are two scripts that need to be included in the end of `<a-head>`.

```markup
<script src="https://raw.githack.com/donmccurdy/aframe-extras/master/dist/aframe-extras.loaders.min.js"></script>
<script src="https://unpkg.com/three@0.95.0/examples/js/libs/inflate.min.js"></script>
```

## Formats

### OBJ

This file is commonly used and straightforward. Check out the [a-obj-model documentation](https://github.com/aframevr/aframe/blob/master/docs/components/obj-model.md) for more information! 

```markup
<a-obj-model src="LINK_TO_OBJ" mtl="LINK_TO_MTL"></a-obj-model>
```

{% hint style="danger" %}
Beware that the MTL file will often point to a texture which is local. Make sure to upload the texture separately, copy the link and update the material reference in the MTL file.
{% endhint %}

### FBX

The filmbox is a proprietary format created by Autodesk for 3d file transfers. The files are generally large but work well. 

```markup
<a-entity animation-mixer="clip: *;" 
    scale="0.005 0.005 0.005"
    position="0 0 -2"
    fbx-model="src: url(https://cdn.glitch.com/c9111e7d-1d31-41a0-8e15-78b57caa9816%2FSilly%20Dancing.fbx?v=1574367405594);"></a-entity>    
```

{% hint style="danger" %}
Sometimes they come with textures _baked_ and work directly, but not always. If the FBX file does not show textures, then if possible ignore it and try another one.
{% endhint %}

It is possible to export complete scenes and use them in A-Frame, however, all objects must be reduced to pure geometry with standard materials applied \(Octane materials will not work\).

### GLTF

Short for GL Transmission Format, glTF is a file format for 3D scenes and models using the JSON standard. It’s very easy to add models to an A-Frame scene, by using the `a-gltf-model` primitive \(there are [loaders for other formats](https://aframe.io/docs/0.8.0/introduction/models.html) as well\).

```markup
<a-gltf-model src="https://cdn.rawgit.com/KhronosGroup/glTF-Sample-Models/29355d23/2.0/CesiumMan/glTF-Binary/CesiumMan.glb">
```

* [https://developers.facebook.com/docs/sharing/3d-posts/glb-tutorials](https://developers.facebook.com/docs/sharing/3d-posts/glb-tutorials)
* [https://blackthread.io/gltf-converter/](https://blackthread.io/gltf-converter/)
* [https://labs.maxon.net/?p=3360](https://labs.maxon.net/?p=3360)
* [https://github.com/facebookincubator/FBX2glTF](https://github.com/facebookincubator/FBX2glTF)

{% hint style="info" %}
Cinema4d has a plugin enabling glTF export: [https://labs.maxon.net/?p=3360](https://labs.maxon.net/?p=3360)
{% endhint %}

