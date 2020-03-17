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

It's extremely tedious migrating to a responsive solution. A quick fix is to simple scale the work so that it appears responsive, but is actually just adjusted in size…

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(220);
  
  responsiveScale(400); // original width

  circle(200, 200, 100);
}

function responsiveScale(w){
  var scaleRatio = (windowWidth > w) ? windowWidth / w : 1;
  scale(scaleRatio, scaleRatio);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

