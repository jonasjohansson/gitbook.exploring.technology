# 2. Entities

Within the `<a-scene>` entities \(think of them as objects\) can be added. There are several types of entities, most with logical names, such as `<a-box>` which unsurprisingly creates a box.

```markup
<a-box color="red" position="0 0 -4"></a-box>
```

To move the box we use the `position` attribute which expects three values; x, y and z. By default the box and the camera are both positioned at the `0 0 0` origin, and so we push the box further away by using a negative value in the z-axis.

It's simple to add more boxes, just make sure to have them in different positions.

```markup
<a-box color="red" position="-1 0 -4"></a-box>
<a-box color="green" position="0 0 -4"></a-box>
<a-box color="blue" position="1 0 -4"></a-box>
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
Notice the `shadow` attribute which will ensure that the entities cast a shadow!
{% endhint %}

