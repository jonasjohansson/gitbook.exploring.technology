# Basics

## [Editor](https://editor.p5js.org/)

![](../../../../.gitbook/assets/p5-editor.png)

* **Sketch.js:** The name of the current file, and the place where code is written. By toggling the arrow just next to the name, a "folder" structure is revealed. New files can be uploaded here, such as images.
* **Preview:** A preview of the code, triggered by clicking **play** or ticking **Auto-refresh**. It is possible to change the size of this window by hovering just where the code and preview meet, then click-and-drag.
* **Console**: A small window at the bottom for debugging; showing error messages or other types of information.
* **Top menu**: Many options here, but most relevant is File &gt; Save and File &gt; Share \(available only after the project has been saved\).

{% hint style="warning" %}
You can change the name of your project next to the Auto-refresh button.
{% endhint %}

## Code

In programming, a function is a named section of a program that performs a specific task. In this sense, a function is a type of procedure or routine. 

Processing has two default functions. `setup()` which happens once, in the beginning, and `draw()` which happens forever, until the sketch is stopped. There is also has a bunch of other functions that can be called, these pre-existing functions will be highlighted in color.

```javascript
function setup(){
    createCanvas(400, 400);
}

function draw(){
    background(220);
}
```

In the default code there is also two other functions: `createCanvas(400,400)` and `background(220)`.  Running this example will give us a canvas with  400 pixels width and height, as well as a gray background. The reason it becomes gray is the number 220, which signifies the value of Red, Green and Blue. Since there is only 1 number, it assumes we are defining the value for all three ie. RGB. We can change this by adding commas:

```javascript
background(220,0,0);
```

{% hint style="info" %}
Notice the semicolon at the end, this tells the code interpreter that the line has ended.
{% endhint %}

