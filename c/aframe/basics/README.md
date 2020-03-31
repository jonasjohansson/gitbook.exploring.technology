# Basics

## Create your scene

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

Include the A-Frame library as a `<script>` in  `<head>` and add the `<a-scene>` in  `<body>`. To remove the VR icon visible in the bottom right we tell `<a-scene>` to hide it using `vr-mode-ui` attribute .

### Adding an entity

Within the `<a-scene>` entities \(think of them as objects\) can be added. There are several types of entities, but let's start with a simple box.

```markup
<a-box color="red" position="0 0 -3"></a-box>
```

The position attribute takes three values; x, y and z. If you are unable to see the box it's likely because the default camera and the box are both positioned at the `0 0 0` origin. We won’t be able to see the box unless we move it using `position`. 

It's simple to add more boxes, just make sure to have them in different positions.

```markup
<a-box color="red" position="-1 0.5 -3"></a-box>
<a-box color="green" position="0 0.5 -3"></a-box>
<a-box color="blue" position="1 0.5 -3"></a-box>
```

{% hint style="info" %}
Apart from `color` and `position` there's also `rotation`, `depth`, `width`, `height` and `scale`.
{% endhint %}

Besides `<a-box>` there's several other entities available, [visit the A-Frame documentation](https://aframe.io/docs/0.9.0/introduction/) and scroll down the menu on the left to see a list of primitives. Here's a few more:

```markup
<a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9" shadow></a-box>
<a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E" shadow></a-sphere>
<a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D" shadow></a-cylinder>
<a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4" shadow></a-plane>
```

{% hint style="info" %}
Notice the _shadow_ attribute which will ensure that the entities cast a shadow!
{% endhint %}

## Create an environment

### Texture

We can apply a texture to our entities with an **image** or **video** using the `src` attribute, just like we would with a normal `<img>` element.

```markup
<a-box src="https://i.imgur.com/mYmmbrp.jpg" position="0 2 -5" rotation="0 45 45"></a-box>
```

{% hint style="info" %}
To tile our texture, we can use the `repeat` attribute. `repeat` takes two numbers, how many times to repeat in the X direction and how many times to repeat in the Y direction \(commonly referred to as U and V for textures\).
{% endhint %}

### Sky

We can add a background with `<a-sky>` that surrounds the scene. `<a-sky>`, which is a material applied to the inside of a large sphere, can be a flat color, a 360° image, or a 360° video.

```markup
<a-sky color="#6EBAA7"></a-sky>
```

360 Panoramas from [Wikimedia Commons](https://commons.wikimedia.org/wiki/Main_Page):

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

