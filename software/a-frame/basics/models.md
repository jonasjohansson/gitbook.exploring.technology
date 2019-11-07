# Models

In order to have 3d models in your scene there are two scripts that need to be included.o

```markup
<script src="//cdn.rawgit.com/donmccurdy/aframe-extras/v4.2.0/dist/aframe-extras.min.js"></script>
<script src="https://unpkg.com/three@0.95.0/examples/js/libs/inflate.min.js"></script>
```

### OBJ

This file is often seen when downloading from 3d asset sites, and loading an object file is  straightforward. Check out the [a-obj-model documentation](https://github.com/aframevr/aframe/blob/master/docs/components/obj-model.md) for more information! 

```markup
<a-obj-model src="object.obj" mtl="object.mtl"></a-obj-model>
```

{% hint style="danger" %}
Beware that the .mtl file will often point to a texture which is local. Make sure to upload the texture separately, copy it's link and update the material reference in the .mtl file.
{% endhint %}

### FBX

The filmbox  is a proprietary format created by Autodesk for 3d file transfers. The files are generally large but contain a lot of useful information and work well! 

```markup
<a-entity animation-mixer="clip: *;" 
    scale="0.005 0.005 0.005"
    position="0 0 -2"
    fbx-model="src: url(https://cdn.glitch.com/a0abdcd7-7215-4b88-8d40-02e289bae501%2FJumping.fbx?v=1569357549964);"></a-entity>    
```

{% hint style="danger" %}
Sometimes they come with textures _baked_ and work directly, but not always. If the .fbx file does not show textures, then if possible ignore it and try another one.
{% endhint %}

It is possible to export complete scenes from Cinema4D or Blender and use them in A-Frame. However, be mindful of the fact that A-Frame does not understand functions such as the Cloner. All objects must be reduced to pure geometry with standard materials applied \(Octane materials will not work\).

### GLTF

**glTF** \(derivative short form of **GL Transmission Format**\) is a file format for [3D scenes and models](https://en.wikipedia.org/wiki/3D_modeling) using the [JSON](https://en.wikipedia.org/wiki/JSON) standard. It is an API-neutral runtime asset delivery format developed by the [Khronos Group](https://en.wikipedia.org/wiki/Khronos_Group) 3D Formats Working Group.

* [https://developers.facebook.com/docs/sharing/3d-posts/glb-tutorials](https://developers.facebook.com/docs/sharing/3d-posts/glb-tutorials)
* [https://blackthread.io/gltf-converter/](https://blackthread.io/gltf-converter/)
* [https://labs.maxon.net/?p=3360](https://labs.maxon.net/?p=3360)
* [https://github.com/facebookincubator/FBX2glTF](https://github.com/facebookincubator/FBX2glTF)

It’s very easy to add models to an A-Frame scene, by using the `a-gltf-model` primitive \(there are [loaders for other formats](https://aframe.io/docs/0.8.0/introduction/models.html) as well\):

```markup
<a-gltf-model src="model.gltf">
```

## Test your model

Verify that your model look and behave as intended using any of the many previewing tools, some of which allows you test various lighting as well as exporting to other formats.

* [https://www.creators3d.com/online-viewer](https://www.creators3d.com/online-viewer)
* [https://www.autodesk.com/products/fbx/fbx-review](https://www.autodesk.com/products/fbx/fbx-review)
* [https://gltf-viewer.donmccurdy.com/](https://gltf-viewer.donmccurdy.com/)
* [https://gltf.insimo.com/](https://gltf.insimo.com/)
* [https://3dviewer.net/](https://3dviewer.net/)

