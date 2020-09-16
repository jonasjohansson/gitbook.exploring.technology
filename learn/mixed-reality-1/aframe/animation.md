# 4. Animation

For animation we can use the `animation` attribute!

```markup
<a-cylinder
  color="orange"
  radius="0.1"
  position="0 2 -2"
  animation="property: rotation; dir: alternate; dur: 2000; loop: true; from: 0 0 0; to: 0 0 360;"
></a-cylinder>
```

| Property | Description |
| :--- | :--- |
| property | Property to animate. Can be a component name, a dot-delimited property of a component \(eg. material.color\) or a plain attribute. |
| from | Initial value at start of animation. If not specified, the current property value of the entity will be used. |
| to | Target value at end of animation. |
| delay | How long \(milliseconds\) to wait before starting. |
| dir | Which direction to go from `from` to `to`. |
| dur | How long \(milliseconds\) each cycle of the animation is. |
| easing | Easing function of animation. To ease in, ease out, ease in and out. See [easings](https://www.npmjs.com/package/aframe-animation-component#easings). |
| loop | How many times the animation should repeat. If the value is `true`, the animation will repeat infinitely. |

You can also add multiple animations:

```markup
<a-cylinder
  color="orange"
  animation="property: rotation; from: 0 0 0; to: 0 0 360"
  animation__radius="property: radius; from: 0.1; to: 0.5"
></a-cylinder>
```

