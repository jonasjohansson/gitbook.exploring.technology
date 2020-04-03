# 13. Audio

Audio in the browser is very powerful and a blast to include in visual projects, check out [Patatap](https://patatap.com/) for an interactive audiovisual browser experience, and visit the [sound reference](https://p5js.org/reference/#/libraries/p5.sound) and [additional examples](https://github.com/processing/p5.js-sound/) to learn more! There's also other "libraries" that are excellent for generating sound, curious for more? Check out [Howler](https://howlerjs.com/) and [Tone](https://tonejs.github.io/).

{% embed url="https://vimeo.com/68161863" %}



{% embed url="https://vimeo.com/95057507" %}

If development is done **outside** of the p5 editor, then include this script…

```markup
<script src="https://unpkg.com/p5@0.10.2/lib/addons/p5.sound.min.js"></script>
```

## Sounds

Playing sounds is simple and fun, and can easily be used together with the statements and variables from before.

```javascript
let song;

function preload() {
  song = loadSound('https://cors-anywhere.herokuapp.com/https://www.soundhelix.com/examples/mp3/SoundHelix-Song-4.mp3');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  background(255, 0, 0);
}

function mousePressed() {
  if (song.isPlaying()) {
    song.stop();
    background(255, 0, 0);
  } else {
    song.play();
    background(0, 255, 0);
  }
}
```

## Synth

What's more fun than playing sound files? Creating the sounds yourself! Ableton has released an interactive learning platform titled Learning Synths, it's fantastic! Check it out to get an idea of what is possible to create in the browser.

{% embed url="https://learningsynths.ableton.com/" %}

{% tabs %}
{% tab title="Envelope" %}
```javascript
let attackLevel = 1.0;
let releaseLevel = 0;

let attackTime = 0.1;
let decayTime = 0.5;
let susPercent = 0.2;
let releaseTime = 0.5;

function setup() {}

function playEnv(type = "triangle", freq = 220) {
  let env = new p5.Envelope();
  env.setADSR(attackTime, decayTime, susPercent, releaseTime);
  env.setRange(attackLevel, releaseLevel);

  let triOsc = new p5.Oscillator(type);
  triOsc.amp(env);
  triOsc.start();
  triOsc.freq(freq);

  env.play();
}

function keyPressed() {
  switch (keyCode) {
    case DOWN_ARROW:
      playEnv("sine", random(0, 110));
      break;
    case LEFT_ARROW:
      playEnv("triangle", random(110, 220));
      break;
    case UP_ARROW:
      playEnv("sawtooth", random(220, 330));
      break;
    case RIGHT_ARROW:
      playEnv("square", random(330, 440));
      break;
  }
}
```
{% endtab %}

{% tab title="MonoSynth" %}
```javascript
function draw() {
  background(255);
  textAlign(CENTER);

  if (getAudioContext().state !== 'running') {
    text('click to start audio', width/2, height/2);
  } else {
    text('audio is enabled', width/2, height/2);
  }
}

function touchStarted() {
  if (getAudioContext().state !== 'running') {
    getAudioContext().resume();
  }
  let synth = new p5.MonoSynth();
  synth.play('A4', 0.5, 0, 0.2);
}
```
{% endtab %}
{% endtabs %}

