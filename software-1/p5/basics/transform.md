# Transform

### Rotation

Use `rotate()` to draw shapes in different angles. Keep in mind, rotation is applied to the “canvas” and not to the shapes you are drawing. Think as if we are rotating the paper we are drawing on. By default, rotation is measure in radians, to use angles type `angleMode(DEGREES)` in **setup** to make life easier.

![](../../../.gitbook/assets/p5-rotate.png)

The amount rotated is also _remembered_ and stacks upon itself. This is clearly seen when adding several squares and applying a rotation to each.

### Translate

If rotation feels complex, welcome to `translate`. A genious function in many ways, but difficult to master; translate moves the whole canvas in x and y, and in conjunction with rotate can make a rectangle spin around itself. Let's try the following code:

```javascript
function setup() {
  createCanvas(400, 400);
  angleMode(DEGREES);
  rectMode(CENTER);
}

function draw() {
  background(220);
  translate(200,200);
  rotate(frameCount);
  square(0,0,200);
}
```

Several new things are happening here:

1. We define the rectangle mode to be CENTER, meaning the  origin of the square is in its centre.
2. We move the canvas 200 pixels from the left and top using translate
3. We rotate the canvas, and instead of a static value, we use **frameCount**. A special variable that increases by 1 every time draw is being called.

![](../../../.gitbook/assets/p5-translate.png)

### Push and Pop

It is possible to _negate_ the effect of a rotation or translate by using the same value but negative, for instance by typing `rotate(-10)` after `rotate(10)`. But, there is also a completely different way of ensuring that functions **only** happen to specific shapes.

Code doesn't have _layers_ like most design software, but we can simulate the effect of a layer using two functions: `push` and `pop`.  Anything that happens inside of these, will not be _seen_ by anyone else. what happens in push and pop, stays in push and pop.

![](../../../.gitbook/assets/p5-pushpop%20%281%29.png)

