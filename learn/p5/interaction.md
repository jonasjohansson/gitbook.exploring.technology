# 10. Interaction

There are several [events](https://p5js.org/reference/#group-Events) that can be "listened" too; button is pressed, mouse is clicked, mobile device is shaken. Some of the events even act as a variable!

{% tabs %}
{% tab title="Mouse" %}
```javascript
function setup() {
  createCanvas(640, 480);
}

function draw() {
  background(220);
  
  if (mouseIsPressed) {
    fill(0);
  } else {
    fill(255);
  }
  
  ellipse(mouseX, mouseY, 80, 80);
};
```
{% endtab %}

{% tab title="Keyboard" %}
```javascript
/* Keycodes: BACKSPACE, DELETE, ENTER, RETURN, TAB, ESCAPE, SHIFT, CONTROL, OPTION, ALT, UP_ARROW, DOWN_ARROW, LEFT_ARROW, RIGHT_ARROW */

let r = 0;
let g = 0;
let b = 0;

function setup(){
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(r,g,b);
  
  if (keyIsDown(UP_ARROW)) {
    r = 255;
    g = 255;
    b = 0;
  } else if (keyIsDown(DOWN_ARROW)) {
    r = 0;
    g = 255;
    b = 255;
  }
}

function keyPressed() {
  if (keyCode === LEFT_ARROW) {
    r = 255;
    g = 255;
    b = 255;
  } else if (keyCode === RIGHT_ARROW) {
    r = 0;
    g = 0;
    b = 0;
  }
}

function keyTyped() {
  if (key === 'r') {
    r = 255;
    g = 0;
    b = 0;
  } else if (key === 'g') {
    r = 0;
    g = 255;
    b = 0;
  } else if (key === 'b') {
    r = 0;
    g = 0;
    b = 255;
  }
  // uncomment to prevent any default behavior
  // return false;
}
```
{% endtab %}

{% tab title="Motion" %}
Due to security restrictions users must give explicit access to motion data. This is normally done by providing a button which upon being clicked prompts the user to for permission.

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
  permission();
}

function draw() {

  // convert rotation to color
  r = map(rotationX, -90, 90, 0, 255);
  g = map(rotationY, -90, 90, 0, 255);
  b = map(rotationZ, -90, 90, 0, 255);

  // convert rotation to position on screen
  posX = constrain(map(rotationY, -90, 90, 0, width), 0, width);
  posY = constrain(map(rotationX, -90, 90, 0, height), 0, height);

  if (mouseIsPressed) {
    fill(r, g, b);
  } else {
    fill(255);
  }

  // count number of individual touch points
  switch (touches.length) {
    case 0:
    case 1:
      ellipse(posX, posY, 100, 100);
      break;
    case 2:
      square(posX - 50, posY - 50, 100);
      break;
  }
}

function touchMoved() {
  return false;
}

function permission() {
  button = createButton("start");
  button.style("position", "absolute");
  button.style("z-index", "9999");
  button.position(windowWidth / 2, windowHeight / 2);
  button.mousePressed(permission);
  if (
    typeof DeviceMotionEvent !== "undefined" &&
    typeof DeviceMotionEvent.requestPermission === "function"
  ) {
    DeviceMotionEvent.requestPermission()
      .then(response => {
        if (response == "granted") {
          button.remove();
        }
      })
      .catch(console.error);
  }
}
```
{% endtab %}

{% tab title="Sound" %}
```javascript
let mic, fft;

function setup() {
  createCanvas(windowWidth, windowHeight);
  noFill();

  mic = new p5.AudioIn();
  mic.start();
  fft = new p5.FFT();
  fft.setInput(mic);
}

function draw() {
  background(200);

  let spectrum = fft.analyze();

  beginShape();
  for (i = 0; i < spectrum.length; i++) {
    vertex(i, map(spectrum[i], 0, width, height, 0));
  }
  endShape();
}
```
{% endtab %}

{% tab title="Speech" %}
```javascript
// https://idmnyu.github.io/p5.js-speech/
// https://github.com/libyal/libfwnt/wiki/Language-Code-identifiers
var myRec = new p5.SpeechRec();
var myVoice = new p5.Speech();

myRec.continuous = true;
myRec.interimResults = true;

function setup() {
  createCanvas(windowWidth, windowHeight);
  myRec.onResult = parseResult;
  myRec.start();
  myVoice.setLang("en-UK");
  myVoice.speak("Name a color");
}

function draw() {}

function parseResult() {
  if (myRec.resultValue === true) {
    let word = myRec.resultString;
    word = word.toLowerCase();
    switch (word) {
      case 'red':
        background(255, 0, 0);
        break;
      case 'green':
        background(0, 255, 0);
        break;
      case 'blue':
        background(0, 0, 255);
        break;
    }
  }
}
```
{% endtab %}

{% tab title="API" %}
API stands for Application Programming Interface and it is used all the time. An API is a software intermediary that allows two applications to talk to each other. In other words, an API is the messenger that delivers your request to the provider that you're requesting it from and then delivers the response back to you.

There are plenty of [Public API's](https://github.com/public-apis/public-apis) out there, some require creating an account and receiving a unique "key", while others are free to use as-is. In the example below, data is fetched and stored in a variable, ready to be used.

```javascript
var weather;

function preload() {
  weather = loadJSON("https://api.openweathermap.org/data/2.5/weather?q=Stockholm&units=metric&APPID=8bc33b55474e0525d2c28707ca934965&");
}

function setup() {
  print(weather);
}

function draw() {
  textSize(32);
  text(weather.main.temp, 10, 30);
}
```
{% endtab %}
{% endtabs %}

