# Sliders

Sometimes you might need to play with a value to find the right one. In order to have more direct feedback, sliders allow you to change a value in your code by dragging the sliders. The code below gives you for example a slider to change translate\(\), rotate\(\) and circle size.

{% embed url="https://codepen.io/mickeyvanolst/pen/mddNJqQ" %}



```javascript
let translateSliderX;
let translateSliderY;
let rotateSlider;
let sizeSlider;

function setup() {
  createCanvas(500,500);
  translateSliderX = createSlider(0, 500, 100);
  translateSliderX.position(10, 10);
  translateSliderX.style('width', '80px');
  
  translateSliderY = createSlider(0, 500, 100);
  translateSliderY.position(10, 30);
  translateSliderY.style('width', '80px');
  
  rotateSlider = createSlider(0, 360, 100);
  rotateSlider.position(10, 50);
  rotateSlider.style('width', '80px');
  
  sizeSlider = createSlider(0, 500, 100);
  sizeSlider.position(10, 70);
  sizeSlider.style('width', '80px');
  
}

function draw() {
  let transX = translateSliderX.value();
  let transY = translateSliderY.value();
  let rot = rotateSlider.value();
  let size = sizeSlider.value();
  background(50);
  
  
  translate(transX, transY);
  
  push();
  rotate(radians(rot));
  
  fill(250);
  rect(0,0, size,size);
  pop();
}
```

