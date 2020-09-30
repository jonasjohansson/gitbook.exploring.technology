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

Read the full list of properties [here](https://www.npmjs.com/package/aframe-animation-component). You can also add multiple animations:

```markup
<a-cylinder
  color="orange"
  animation="property: rotation; from: 0 0 0; to: 0 0 360"
  animation__radius="property: radius; from: 0.1; to: 0.5"
></a-cylinder>
```

