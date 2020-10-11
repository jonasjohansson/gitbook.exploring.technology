# 7. Text

{% hint style="success" %}
Use the [A-Frame Troika Text](https://github.com/lojjic/aframe-troika-text) for custom type and much more!
{% endhint %}

Rendering text in 3D is not trivial, but the `<a-text>` component make things breezy.

```markup
<a-text value="AaBb"
        position="0 1 -2"
        color="red"
        align="center">
</a-text>
```

By adding the above in your `<a-scene>` you will see a text block which can be used just like any other entity. It comes with a [bunch of attributes and configuration](https://aframe.io/docs/0.9.0/components/text.html):

| Attribute | Default |
| :--- | :--- |
| align | left |
| color | \#fff |
| font | roboto |

### Background

In situations where you require a background color to make the text legible, add a `plane` or `box` geometry with a coloured material. To have the geometry automatically scale with the text, set the geometry component’s `width` and `height` properties to`auto`.

```markup
<a-text value="And as he was falling down the cliff he thought 'Finally, something is happening to me!'"
        position="0 1 -2"
        color="white"
        geometry="primitive: plane; width: auto; height: auto"
        material="color: black"
        align="left">
</a-text>
```

### Text geometry

You may have noticed that the previous example lack 3d geometry. Luckily, the [A-Frame Text Geometry Component](https://www.npmjs.com/package/aframe-text-geometry-component) can remedy this situation along with the [Facetype font converter](http://gero3.github.io/facetype.js/) \(follow the same steps as above but using this site instead\). 

```markup
<script src="https://unpkg.com/aframe-text-geometry-component@^0.5.0/dist/aframe-text-geometry-component.min.js"></script> 
```

Create an entity using the new component and reference the new JSON type file, no fontImage needed:

```markup
<a-entity
    text-geometry="value: EeFf; font: YOUR_JSON;"
    material="color: orange">
</a-entity>
```

