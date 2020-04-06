# 3. Environment

### Texture

We can apply a texture to our entities with an **image** or **video** using the `src` attribute, just like we would with a normal `<img>` element.

```markup
<a-box src="https://i.imgur.com/mYmmbrp.jpg" position="0 3 -3" rotation="0 45 45"></a-box>
```

{% hint style="info" %}
To tile our texture, we can use the `repeat` attribute. `repeat` takes two numbers, how many times to repeat in the X direction and how many times to repeat in the Y direction \(commonly referred to as U and V for textures\).
{% endhint %}

### Sky

We can add a background with `<a-sky>` that surrounds the scene, and provide a color or set a texture.

```markup
<a-sky color="#CCC"></a-sky>
```

360 panoramic images can be found at [Wikimedia Commons](https://commons.wikimedia.org/wiki/Main_Page):

* [Halde Zollern](https://commons.wikimedia.org/wiki/File:Halde_Zollern_Panorama_01.jpg)
* [Lake Byllesby Regional Park](https://commons.wikimedia.org/wiki/File:Lake_Byllesby_Regional_Park_-_360%C2%B0_Equirectangular_Street_View_Photo_%2827332591527%29.jpg)
* [Kloster Paulinzella, Thüringen](https://commons.wikimedia.org/wiki/File:Kloster_Paulinzella,_Th%C3%BCringen,_360x180,_170316,_ako_%281%29.jpg)
* [Tiger And Turtle, Duisburg](https://commons.wikimedia.org/wiki/File:Tiger_And_Turtle_Panorama.jpg)
* [Zapporthorn, Switzerland](https://commons.wikimedia.org/wiki/File:Zapporthorn_Spherical_Panorama.jpg)
* [Naturalis Biodiversity Center](https://commons.wikimedia.org/wiki/File:Naturalis_Biodiversity_Center_-_Museum_-_Exhibition_Primeval_parade_33_-_Overview_room_with_skeletons_-_Panorama_360_3D.jpg)

### Ground

To add a ground, we can use `<a-plane>`. By default, planes are oriented parallel to the XY axis. To make it parallel to the ground, we need to orient it along the XZ axis. We can do so by rotating the plane negative 90° on the X-axis. 

```markup
<a-plane rotation="-90 0 0" color="gray" width="30" height="30" ></a-plane>
```

We’ll want the ground to be large, so we can increase the `width` and `height`. Let’s make it 30-meters in each direction:

Then we can apply an image texture to our ground:

```markup
<a-plane src="https://cdn.aframe.io/a-painter/images/floor.jpg" rotation="-90 0 0" width="30" height="30"></a-plane>
```

### Lighting

We can change how the scene is lit by using `<a-light>`. By default if we don’t specify any lights, A-Frame adds an ambient light and a directional light. If A-Frame didn’t add lights for us, the scene would be black. Once we add lights of our own, however, the default lighting setup is removed and replaced with our setup.

```markup
<a-light type="ambient" color="red"></a-light>
<a-light type="point" intensity="2" position="0 0 -2"></a-light>
```

### Assets

Instead of adding the textures above directly as sources we can use A-Frame's builtin asset system. This keeps the code clean and also tells the system to wait with showing all the assets until they have all loaded.

```markup
<a-assets>
  <img id="skyTexture"
  src="https://cdn.aframe.io/360-image-gallery-boilerplate/img/sechelt.jpg">
 </a-assets>
 <a-sky src="#skyTexture"></a-sky>
```

{% hint style="info" %}
Add `shader="standard"` to `a-sky` in order to have it react to the lighting in the scene.
{% endhint %}

