# P5js

Want to create a generative Frankenstein? Here you go, Processing and A-Frame working together!

{% tabs %}
{% tab title="index.html" %}
```markup
<html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <script src="https://aframe.io/releases/0.9.2/aframe.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/p5.min.js"></script>
    <script src="sketch.js"></script>
    <style>
      canvas#defaultCanvas0 {
        position:fixed;
        top:0;
        left:0;
        z-index:2;
      }
    </style>
  </head>
  <body>
    <a-scene>
      <a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9" shadow></a-box>
      <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E" shadow></a-sphere>
      <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D" shadow></a-cylinder>
      <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4" shadow></a-plane>
    </a-scene>
  </body>
</html>

```
{% endtab %}

{% tab title="script.js" %}
```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  if (mouseIsPressed) {
    fill(0);
  } else {
    fill(255);
  }
  ellipse(mouseX, mouseY, 80, 80);
}
```
{% endtab %}
{% endtabs %}



