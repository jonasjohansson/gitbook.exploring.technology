# Interaction

There are several [events](https://p5js.org/reference/#group-Events) that can be "listened" too; button is pressed, mouse is clicked, mobile device is shaken. Some of the events even act as a variable!

## Mouse

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

## Keyboard

…

## Motion

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

## Speech

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

## API

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

