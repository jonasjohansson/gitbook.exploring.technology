# 2. Entities

Within `<a-scene>` entities can be added. There are several types of entities, most with logical names, such as `<a-box>` which unsurprisingly creates a box.

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

### Parenting & Null object

Notice how the box has a start `<a-box>` and end `</a-box>` tag which implies there can be content inside \(turning the box into a parent, and whatever is inside to its children\). Just like how the boxes are inside `<a-scene>` other entities can be placed in the boxes.  For instance, it could be smart to create an "empty" `<a-entity>` that just sets the position in the z-axis. This way it would be possible to control all the boxes position by changing one parameter. An empty entity can also be understood as a Null object \(famous in 3d software\).

```markup
<a-entity position="0 0 -4">
    <a-box color="red" position="-1 0 0"></a-box>
    <a-box color="green" position="0 0 0"></a-box>
    <a-box color="blue" position="1 0 0"></a-box>
</a-entity>
```

{% hint style="info" %}
Apart from `color` and `position` there's also `rotation`, `depth`, `width`, `height` and `scale`.
{% endhint %}

### Other entities

Besides `<a-box>` there's several other entities available, [visit the A-Frame documentation](https://aframe.io/docs/0.9.0/introduction/) and scroll down the menu on the left to see a list of primitives. Here's a few more:

```markup
<a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9" shadow></a-box>
<a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E" shadow></a-sphere>
<a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D" shadow></a-cylinder>
<a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4" shadow></a-plane>
```

{% hint style="info" %}
Notice the `shadow` attribute which will ensure that the entities cast a shadow! Set the type of shadow by using `shadow="type: pcfsoft"` on `<a-scene>` and the options **basic**, **pcf** and **pcsoft**.
{% endhint %}

While not mandatory, it is important to know that `<a-box>` is a simplified version of writing `<a-entity geometry="primitive: box">`.

### Is this coding?

There are several level of abstractions of code. At the bottom, you have the electrical components which are either on \(1, true\), or off \(0, false\). Then, you have machine language, series of commands that tell electrical components how to behave. 

Since machine language is very complex, a layer on top has been written to make it easier. You can think of this layer as the Operative System \(Windows, Mac, Linux\). And once you're in the OS there's plenty of types of languages of code which can be used: C++, Python, Java and JavaScript, which is used in the browser.

So, all the way from the electrical component we have finally reached A-Frame, which uses a combination of HTML and JavaScript. HTML is known is a markup language, meaning, it uses special building blocks to define how the content of a website is displayed. A-Frame has taken advantage of this, and created their own blocks, that through JavaScript, define the 3D scene.

Using A-Frame, you are definitely coding, it just looks a bit different than how coding is normally presented. But rest assured, there are several ways of coding, some that  don't even require typing.

