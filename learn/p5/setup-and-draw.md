# 2. Setup and Draw

Processing has two default functions: `setup()` which happens once, and `draw()` which goes on forever, until the sketch is stopped.  A function is a named section of a program that performs a specific task. In this sense, a function is a type of procedure or routine.

```javascript
function setup(){
    createCanvas(400, 400);
}

function draw(){
    background(220); // gray
}
```

In our case there is also two additional functions: `createCanvas()` and `background()`which will display a 400 pixels wide and high canvas, with a gray background. The number 220, when alone, define the grayscale value \(0 = black, 255 = white\). If two more values were to be added the numbers would define the amount of Red, Green and blue.

```javascript
background(220,0,0); // red
```

## Related links

* [setup\(\)](https://p5js.org/reference/#/p5/setup)
* [draw\(\)](https://p5js.org/reference/#/p5/draw)
* [background\(\)](https://p5js.org/reference/#/p5/background)

