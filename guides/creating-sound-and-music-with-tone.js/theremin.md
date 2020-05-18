# 3. Theremin

One of the first synthesizers created was the Theremin, invented by [Leon Theremin](https://en.wikipedia.org/wiki/Leon_Theremin). It consists of two metal bars that senses how far away your hands are, where one of them controls pitch and the other volume.

{% embed url="https://www.youtube.com/watch?v=w5qf9O6c20o" %}

Beautiful! [This one](https://www.youtube.com/watch?v=pSzTPGlNa5U) isn't that bad either. Let's build one ourselves!

### Creating a volume control

We already have our oscillator going. The oscillator has a built-in frequency control, so our right arm is already set to go. What we need now is the volume control using [`Tone.Gain`](https://tonejs.github.io/docs/13.8.25/Gain)

```javascript
const volume = new Tone.Gain({ gain: 0.2 })
```

Routing our oscillator through this `volume` control will now play at a lower volume.

```javascript
function setup() {
  Tone.Master.volume.value = -24

  const osc = new Tone.Oscillator({ frequency: 440 })
  const volume = new Tone.Gain({ gain: 0.2 })
  osc.connect(volume)
  volume.connect(Tone.Master)
  osc.start()
}
```

#### Understanding Gain

Gains go linearly between `0` and `1`, whereas volumes in decibels are logarithmic and usually spans from `-Infinity` to `0` \(full volume\). `-24` above is roughly like having 50% volume in a music player.

### Playing the thing

It's time to express ourselves. We will control the Theremin by mapping the mouse `y` position to the pitch and its `x` position to the volume.

First we need a canvas spanning across the window for optimal control:

```javascript
function setup() {
  createCanvas(window.innerWidth, window.innerHeight)
  // ...
}
```

Then to map the mouse positions we use the `mouseMoved()` function. Since `width` and `height` is the full window dimensions, we'll easily map the mouse position to a number between `0` and `1`.

```javascript
function mouseMoved() {
  // This gives us a range of 0 to 1000 Hz
  osc.frequency.value = 1000 * mouseY / height
  // This gives us a gain of 0 to 1
  volume.gain.value = mouseX / width
}
```

Hold your horses now, this will blow up! `osc` and `volume` are not accessible from inside `mouseMoved()`, as they were created inside `setup()` and stuck in that scope.

 Let's go from local to global:

```javascript
let osc
let volume

function setup() {
  // ...
  osc = new Tone.Oscillator({ frequency: 440 })
  volume = new Tone.Gain({ gain: 0.2 })
  // ...
}
```

Phew, that's looking better!

### Toggling the oscillator using the keyboard

The last thing we'll do is to have the oscillator start and stop using the keyboard. Pressing a key will start it and releasing that key will stop it. We'll utilize the `keyPressed()` and `keyReleased()` functions for this.

```javascript
function keyPressed() {
  osc.start()
}

function keyReleased() {
  osc.stop()
}
```

{% hint style="info" %}
You'll need to click on the canvas for it to start recognizing key strokes.
{% endhint %}

Here's the final code:

```javascript
let osc
let volume

function setup() {
  createCanvas(window.innerWidth, window.innerHeight)

  Tone.Master.volume.value = -24

  osc = new Tone.Oscillator()
  volume = new Tone.Gain()
  osc.connect(volume)
  volume.connect(Tone.Master)
}

function keyPressed() {
  osc.start()
}

function keyReleased() {
  osc.stop()
}

function mouseMoved() {
  osc.frequency.value = 1000 * mouseY / height
  volume.gain.value = mouseX / width
}
```

Now give it a go, and remember to play from your heart.

