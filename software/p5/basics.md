# Basics

## Editor

Find the editor by going to [https://editor.p5js.org](https://editor.p5js.org). Create your account if you haven’t already and log in.

#### **Sketch.js**

This is where code is written. on the left, 

#### **Preview**

A preview of the code, triggered by clicking **play** or ticking **Auto-refresh**.

#### Console

A small window at the bottom for debugging; showing error messages or other types of information.

{% hint style="warning" %}
You can change the name of your project next to the Auto-refresh button.
{% endhint %}

**Top menu**

* To save your changes, go to File &gt; Save \(CMD+S\)

### Code

In programming, a function is a named section of a program that performs a specific task. In this sense, a function is a type of procedure or routine. 

```javascript
function setup(){
    createCanvas(400, 400);
}

function draw(){
    background(220);
}
```

Processing has two default functions. `setup()` which happens once, in the beginning, and `draw()` which happens forever, until the sketch is stopped. There is also has a bunch of other functions that can be called, these pre-existing functions will be highlighted in color.

In this default example there is also two other functions: `createCanvas(400,400)` and `background(220)`.  Running this example will give us a canvas with  400 pixels width and height, as well as a gray background. The reason it becomes gray is the number 220, which signifies the value of Red, Green and Blue. Since there is only 1 number, it assumes we are defining the value for all three ie. RGB. We can change this by adding commas:

```javascript
background(220,0,0);
```

{% hint style="info" %}
Notice the semicolon at the end, this tells the code interpreter that the line has ended.
{% endhint %}

## Shapes

Let us begin drawing by adding a circle. The circle function takes three parameters: x, y and diameter. Type the following **inside draw**:

```javascript
circle(200,200,300);
```

The first two values tell the circle where to be, and the last provides the diameter.  In our case, this will place the circle in the middle of the canvas, as the circle has its centre as point of origin. In this situation 200 pushes the circle centre from the left and top.

It is highly recommended to read up on each function using the [Processing References](https://processing.org/reference/), as they are not all the same.

