# Sliders

Mastering transformation will be one of many keys to making generative visuals! Try this example that uses sliders to further explain the concept of transform, rotate and push and pop:

{% embed url="https://codepen.io/mickeyvanolst/pen/mddNJqQ" %}

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
  sliderTranslateX = createSlider(0, width, width / 2);
  sliderTranslateX.position(10, 10);

  sliderTranslateY = createSlider(0, height, height / 2);
  sliderTranslateY.position(10, 30);

  sliderRotation = createSlider(0, 360, 180);
  sliderRotation.position(10, 50);

  sliderSize = createSlider(0, width, width / 2);
  sliderSize.position(10, 70);
  
  rectMode(CENTER); // try removing this
}

function draw() {
  background(220);
  
  let tx = sliderTranslateX.value();
  let ty = sliderTranslateY.value();
  let rot = sliderRotation.value();
  let size = sliderSize.value();

  translate(tx, ty);

  rotate(radians(rot));
  rect(0, 0, size, size);
}
```

