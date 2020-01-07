# Responsive

When the sketch needs to work on multiple screen sizes setting a fixed canvas size is no good. There are predefined variables such as `windowWidth` and `windowHeight` that will automatically get the value of the current device.

```javascript
function setup(){
    createCanvas(windowWidth, windowHeight);
}
```

For the canvas to resize together with the window, a special function is added that is triggered any time the window is resized.

```javascript
function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

### Scale trick

If a lot of work has gone into a design where the canvas width was originally fixed, it's extremely tedious migrating into a responsive solution.



```javascript
function draw() {
  background(220);
  
  var scaleRatio = (windowWidth < w) ? w / windowWidth : windowWidth / w;
  
  scale(scaleRatio, scaleRatio);

  circle(200,200,100);
}
```

