# 6. Lines and Curves

## Line

Draw a line using `line(x1,y1,x2,y2)` where x1/y1 define the start and x2/y2 the end. 

```javascript
function draw() {
  line(100, 200, 100, 300);
}
```

## Triangle

Draw a triangle using `triangle(x1,y1,x2,y2,x3,y3)`. Notice the additional x3/y3.

```javascript
function draw() {
  triangle(100, 100, 150, 25, 200, 100);
}
```

## Polygons

Draw polygons \(means basically "many sides"\). The number of sides are defined by the amount of vertices and are added using `vertex(x,y`\). Type `beginShape()` to signify that a new shape will begin. Add the vertices, and close with `endShape()`. Make the final vertex identical to the start vertex to "close" the shape.

```javascript
function draw() {
  beginShape();
  vertex(100, 0);
  vertex(5, 70);
  vertex(40, 180);
  vertex(160, 180);
  vertex(195, 70);
  vertex(100, 0); 
  endShape();
}
```

## Curves

Curves are trickier… to get started use `curveVertex(x,y)` . The first and last vertices define the direction, as illustrated by the two lines.

```javascript
function draw() {
  line(100, 200, 100, 300);
  line(300, 200, 300, 300);

  beginShape();
  curveVertex(100, -500);
  curveVertex(100, 200);
  curveVertex(300, 200);
  curveVertex(300, -500);
  endShape();
}
```

It is also possible to use `bezier()` and `curve()` but these are much more complex to understand and use, as they include the bezier curve values within the function, making it difficult to read.

```javascript
function draw() {
  noFill();
  stroke(255, 100, 0);
  line(300, 10, 10, 10);
  line(300, 300, 0, 300);
  stroke(0, 0, 0);
  bezier(300, 10, 10, 10, 300, 300, 0, 300);
}
```

## Related links

* [line\(\)](https://p5js.org/reference/#/p5/line)
* [triangle\(\)](https://p5js.org/reference/#/p5/triangle)
* [beginShape\(\)](https://p5js.org/reference/#/p5/beginShape)
* [vertex\(\)](https://p5js.org/reference/#/p5/vertex)
* [endShape\(\)](https://p5js.org/reference/#/p5/endShape)
* [bezier\(\)](https://p5js.org/reference/#/p5/bezier)
* [curve\(\)](https://p5js.org/reference/#/p5/curve)

