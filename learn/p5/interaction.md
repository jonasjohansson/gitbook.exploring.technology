# 13. Interaction

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

```javascript
function setup(){
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  if (keyIsDown(UP_ARROW)) {
    background(255,0,0);
  } else if (keyIsDown(DOWN_ARROW)) {
    background(0,255,0);
  }
}

function keyPressed() {
  if (keyCode === LEFT_ARROW) {
    background(0,0,255);
  } else if (keyCode === RIGHT_ARROW) {
    background(255,0,255);
  }
}
```

## Sound



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

## Speech

For this to work, include [https://raw.githack.com/IDMNYU/p5.js-speech/master/lib/p5.speech.js](https://raw.githack.com/IDMNYU/p5.js-speech/master/lib/p5.speech.js).

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



