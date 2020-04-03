# 2. Setup and Draw

Processing has two default functions. `setup()` which happens once, in the beginning, and `draw()` which happens forever, until the sketch is stopped.  A function is a named section of a program that performs a specific task. In this sense, a function is a type of procedure or routine.

```javascript
function setup(){
    createCanvas(400, 400);
}

function draw(){
    background(220); // gray
}
```

In the default code there is also two additional functions: `createCanvas(400, 400)` and `background(220)`. Running this will give us a canvas 400 pixels wide and high, with a gray background. The number 220, when alone, signifies the amount of _lightness_ ****in the scene. If two more values were to be added the numbers would define the amount of Red, Green and blue.

```javascript
background(220,0,0); // red
```

{% hint style="info" %}
Notice the semicolon at the end, this tells the code interpreter that the line has ended.
{% endhint %}

