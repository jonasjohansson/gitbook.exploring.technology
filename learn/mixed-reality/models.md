# 5. Models

Build you own model using or download from an online repository.  Use the [Online Viewer](https://www.creators3d.com/online-viewer) to verify the file works \(drag and drop\).

| Services | Type |
| :--- | :--- |
| [Blender](https://www.blender.org/) | Production |
| [Cinema4d](https://www.maxon.net/en-us/products/cinema-4d/overview/) | Production |
| [Thingiverse](https://www.thingiverse.com/) | Objects |
| [Sketchfab](https://sketchfab.com/search?features=downloadable+animated&q=low+poly&sort_by=-pertinence&type=models) | Objects |
| [Poly](https://poly.google.com/) | Objects |
| [Mixamo](https://www.mixamo.com/) | Characters & Animation |

## Formats

There are [several formats](https://www.marxentlabs.com/3d-file-formats/) available with [OBJ](https://www.marxentlabs.com/obj-files/), [FBX](https://www.marxentlabs.com/fbx-files/) and [GLTF](https://www.marxentlabs.com/gltf-files/)/[GLB](https://www.marxentlabs.com/glb-files/) being the most popular. To learn about them in detail, and others, [read these articles](https://www.marxentlabs.com/defy-reality-the-3d-commerce-blog/).

{% tabs %}
{% tab title="OBJ" %}
This file is commonly used and straightforward. Check out the [a-obj-model documentation](https://github.com/aframevr/aframe/blob/master/docs/components/obj-model.md) for more information! 

```markup
<a-obj-model src="LINK_TO_OBJ" mtl="LINK_TO_MTL"></a-obj-model>
```

* [Skyscraper.obj](https://people.sc.fsu.edu/~jburkardt/data/obj/skyscraper.obj)

{% hint style="danger" %}
Be aware that the MTL file will often point to a local texture. Make sure to upload the texture separately, copy the link and then open the MTL file in a text editor and change the local reference to the uploaded link.
{% endhint %}
{% endtab %}

{% tab title="FBX" %}
Filmbox is a proprietary format created by Autodesk for 3d file transfers with support for scenes and animations. In order to use these files two scripts need to be included in `<head>`.

```markup
<script src="https://unpkg.com/aframe-extras@6.1.0/dist/aframe-extras.loaders.min.js"></script>
<script src="https://unpkg.com/three@latest/examples/js/libs/inflate.min.js"></script>
```

Then add the &lt;a-entity&gt; below, referencing your FBX file.

```markup
<a-entity fbx-model="src: url(LINK_TO_FBX);" animation-mixer="clip: *;"></a-entity>    
```

It is possible to export complete scenes and use them in A-Frame, however, all objects must be reduced to pure geometry with standard materials applied \(Octane materials will not work\).
{% endtab %}

{% tab title="GLTF/GLB" %}
Short for GL Transmission Format, GLTF is a file format for 3D scenes and models using the JSON standard. It’s very easy to add models to an A-Frame scene, by using the `a-gltf-model` primitive \(there are [loaders for other formats](https://aframe.io/docs/0.8.0/introduction/models.html) as well\).

```markup
<a-gltf-model src="LINK_TO_GLTF/GLB"></a-gltf-model>
```

* [CesiumMan.glb](https://cdn.rawgit.com/KhronosGroup/glTF-Sample-Models/29355d23/2.0/CesiumMan/glTF-Binary/CesiumMan.glb)

{% hint style="success" %}
Sometimes GLTF comes with a BIN file and a folder of textures. Use this [GLTF to GLB Packer](https://glb-packer.glitch.me/) \([alternative](https://products.aspose.app/3d/conversion/gltf-to-glb)\) to bundle them all into a new file.
{% endhint %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Read the [Troubleshooting page](https://aframe.io/docs/1.0.0/introduction/models.html#troubleshooting) from A-Frame which covers several of the most common pitfalls.
{% endhint %}

