# 9. Randomness

Creating unique moments is both easy and difficult for machines. The `random(min,max)` function at least provides a way to get some kind of randomness.

```javascript
void draw(){
    background(random(255),random(128,192),0);
}
```

## Noise

{% embed url="https://genekogan.com/code/p5js-perlin-noise/" %}

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
  colorMode(HSB, 360, 100, 100, 100);
  angleMode(DEGREES);
}

function draw() {
  clear();
  drawWave(0, 0, width, height);
  noLoop();
}

function keyPressed() {
  redraw();
}

// @reona396
function drawWave(x, y, w, h) {
  const themeColor = random(360);
  const wavesNum = 2;

  fill(themeColor, random(30, 100), random(80, 100));
  noStroke();
  rect(0, 0, w, h);

  for (let i = 0; i < wavesNum; i++) {
    const hue = i % 2 ? themeColor : (themeColor + 180) % 360;
    const saturation = random(30, 100);
    const brightness = random(80, 100);
    const ox = random(-w / 2, w / 2);
    const oy = 0;
    let x, y;
    const yStepA = floor(random(1, 6));
    const yStepB = floor(random(1, 6));
    let xoff = 0.0;
    let xoffStep = random(0.005, 0.02)

    fill(hue, saturation, brightness);

    push();
    translate(ox, oy);
    beginShape();
    for (y = 0; y <= h; y += yStepA) {
      x = map(noise(xoff), 0, 1, 0, w);
      curveVertex(x, y);
      xoff += xoffStep;
    }
    for (y = h; y >= 0; y -= yStepB) {
      x = map(noise(xoff), 0, 1, 0, w);
      curveVertex(x, y);
      xoff += xoffStep;
    }
    endShape();
    pop();
  }
}
```

![](../../../.gitbook/assets/noise%20%281%29.png)

