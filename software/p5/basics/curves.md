# Curves

It is possible to make curved lines, and to turn them into a shape! The function `curveVertex()` takes 2 parameters: x and y.

```javascript
strokeWeight(5);
point(84, 91);
point(68, 19);
point(21, 17);
point(32, 91);
strokeWeight(1);
function draw() {
  var time = millis()/1000;
  var sine = sin(time);
  var mapped = map(sine,-1,1,0,255);
  print('Mapped value: '+mapped);
  background(mapped,0,0);
}
```

