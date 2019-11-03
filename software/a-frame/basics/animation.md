# Animation

It is possible to add the component "animation" to all our entities.

```markup
<a-cylinder color="orange" radius="0.1" position="0 2 -5"
     animation="property: position; dir: alternate; dur: 2000;
          easing: easeInSine; loop: true; to: 0 3 -5"></a-cylinder>
```

We tell `<a-animation>` to:

* Animate the position _attribute_.
* Alternate the _direction_ of the animation on each repeated cycle of the animation.
* Last for 2000 millisecond _duration_ on each cycle.
* Animate _to_ `0 3. -5` which is 100 centimeters higher.
* _Repeat_ the animation indefinitely.

You can also add multiple animations:

```markup
<a-cylinder color="orange" radius="0.1" position="0 2 -5"
     animation="property: to: 0 3 -5"
     animation__radius="property: radius; to: 0.5"></a-cylinder>
```

| Property | Description | Default Value | Values |
| :--- | :--- | :--- | :--- |
| property | Property to animate. Can be a component name, a dot-delimited property of a component \(e.g., `material.color`\), or a plain attribute. |  |  |
| from | Initial value at start of animation. If not specified, the current property value of the entity will be used \(will be sampled on each animation start\). It is best to specify a `from` value when possible for stability. | null |  |
| to | Target value at end of animation. | null |  |
| delay | How long \(milliseconds\) to wait before starting. | 0 |  |
| dir | Which direction to go from `from` to `to`. | normal | alternate, reverse |
| dur | How long \(milliseconds\) each cycle of the animation is. | 1000 |  |
| easing | Easing function of animation. To ease in, ease out, ease in and out. | easeInQuad | See [easings](https://www.npmjs.com/package/aframe-animation-component#easings) |
| loop | How many times the animation should repeat. If the value is `true`, the animation will repeat infinitely. | 0 |  |
| enabled | Toggle startEvents effect. |  |  |

