# Basics

## Create your scene

{% tabs %}
{% tab title="" %}
```markup
<html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <script src="https://aframe.io/releases/0.9.2/aframe.min.js"></script>
  </head>
  <body>
    <a-scene>
    </a-scene>
  </body>
</html>
```
{% endtab %}
{% endtabs %}

 

We include A-Frame as a script tag in the `<head>`. This has to be included _before_ the `<a-scene>`. Next, we include `<a-scene>` in the `<body>`.

{% hint style="info" %}
Notice `<meta name="viewport">` in the top! It ensures that content will look as expected on mobile devices.
{% endhint %}

If you want to remove the VR icon that is visible in the bottom right you have to tell the `<a-scene>` specifically to hide it by using the attribute "vr-mode-ui".

```markup
<a-scene vr-mode-ui="enabled: false">
```

### Adding an entity

Within our `<a-scene>`, we attach _entities_ using one of A-Frame’s standard [primitives](https://aframe.io/docs/0.8.0/primitives/) `<a-box>`. We can use `<a-box>` just like a normal HTML element, defining the tag and using HTML attributes to customise it.

```markup
<a-box color="red" position="0 0 -3"></a-box>
```

{% hint style="info" %}
If you are unable to see the box it's likely because default camera and the box are positioned at the `0 0 0` origin, we won’t be able to see the box unless we move it using `position`. 
{% endhint %}

{% hint style="info" %}
`Position`takes a coordinate value as three space-delimited numbers.   
Negative X axis extends left. Positive X axis extends right.   
Negative Y axis extends down. Positive Y axis extends up.   
Negative Z axis extends in. Positive Z axis extends out.
{% endhint %}

It's simple to add more boxes, just make sure to have them in different positions so they don't overlap.

```markup
<a-box color="red" position="-1 0.5 -3"></a-box>
<a-box color="green" position="0 0.5 -3"></a-box>
<a-box color="blue" position="1 0.5 -3"></a-box>
```

{% hint style="info" %}
Apart from `color` and `position` there's also `rotation`, `depth`, `width`, `height` and `scale`.
{% endhint %}

Besides &lt;a-box&gt; there's several other primitives available. [Visit the A-Frame documentation](https://aframe.io/docs/0.9.0/introduction/) to see what else is and scroll down the menu on the left to see a list of primitives that come with A-Frame. Here's a few more.

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

### Ground

To add a ground, we can use `<a-plane>`. By default, planes are oriented parallel to the XY axis. To make it parallel to the ground, we need to orient it along the XZ axis. We can do so by rotating the plane negative 90° on the X-axis.

```markup
<a-plane rotation="-90 0 0"></a-plane>
```

We’ll want the ground to be large, so we can increase the `width` and `height`. Let’s make it 30-meters in each direction:

```markup
<a-plane rotation="-90 0 0" width="30" height="30"></a-plane>
```

Then we can apply an image texture to our ground:

```markup
<a-plane src="https://cdn.aframe.io/a-painter/images/floor.jpg" rotation="-90 0 0" width="30" height="30"></a-plane>
```

### Sky

We can add a background with `<a-sky>` that surrounds the scene. `<a-sky>`, which is a material applied to the inside of a large sphere, can be a flat color, a 360° image, or a 360° video. For example, a dark gray background would be:

```markup
<a-sky color="#6EBAA7"></a-sky>
```

### Lighting

We can change how the scene is lit by using `<a-light>`. By default if we don’t specify any lights, A-Frame adds an ambient light and a directional light. If A-Frame didn’t add lights for us, the scene would be black. Once we add lights of our own, however, the default lighting setup is removed and replaced with our setup.

```markup
<a-light type="ambient" color="#445451"></a-light>
<a-light type="point" intensity="2" position="2 4 4"></a-light>
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



