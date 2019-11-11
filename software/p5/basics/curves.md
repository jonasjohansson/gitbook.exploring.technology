# Curves

It is possible to make curved lines using `curveVertex()` and then turn them into a shape!

```javascript
function draw() {
  background(220);
  strokeWeight(5);
  point(84, 91);
  point(68, 19);
  point(21, 17);
  point(32, 91);
  strokeWeight(1);
  fill(255, 0, 0);
  beginShape();
  curveVertex(84, 91);
  curveVertex(84, 91);
  curveVertex(68, 19);
  curveVertex(21, 17);
  curveVertex(32, 91);
  curveVertex(32, 91);
  endShape();
}
```

It is also possible to use `bezier()` and `curve()` but these are much more complex to understand and use. At your own risk!

```javascript
function draw() {
    noFill();
    stroke(255, 102, 0);
    line(85, 20, 10, 10);
    line(90, 90, 15, 80);
    stroke(0, 0, 0);
    bezier(85, 20, 10, 10, 90, 90, 15, 80);
}
```

