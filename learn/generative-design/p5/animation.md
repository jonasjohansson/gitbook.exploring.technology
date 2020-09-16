# 8. Animation

It’s possible to use time as a variable for creating events that happen after a certain amount of time, or for animations.

## FrameCount

Ever heard about Frames Per Second \(FPS\)? It is the amount of frames, or updates, that happen during 1 second. So, if an animation goes from 0 to 90 in steps of 1, it would take 3 seconds for it to finish!

The `frameCount` variable provides a way to keep count of how many frames have passed , and it can be used for animation!

```javascript
function draw() {
  square(frameCount,0,10,10);
}
```

It's not great for smooth animations, but whenever the change is in steps of 1 or more, frameCount is a great choice! For smoothness, let's look further…

{% hint style="info" %}
Notice that there is no `background()` in the example. This means that there is no visual "reset" and the canvas is not painted over.
{% endhint %}

## Millis

Our good friend  `millis()` counts the amount of **milliseconds** that has transpired since the sketch began running. We can understand this better by creating a variable, and printing it to the console:

```javascript
function draw() {
  var time = millis();
  print('Time elapsed: '+time);
}
```

After 5 seconds, _time_  will have reached 5000. To use time to control the amount of red in the background we would have to divide it:

```javascript
function draw() {
  var time = millis();
  var red = time/40;
  background(red,0,0);
}
```

## Sin and cos

Since time \(in programming\) only goes forward it’s great for creating timers and all kinds of things, but it can’t reverse. So if we want our background to go back and forth we can use `sin()` and `cos()` which creates a sine and cosine wave.

![](https://lh3.googleusercontent.com/e-BDb0YwSPabn_2B5TgoKADAIPg6riF8YJNRPPFBdxQULQ68bRMJdlbJqQjAtrUlqAunOrBqZt7j7ReHUzGi45uM2n2PiOz8MfK6Bd4TBCt04Wwt_plugKpSEjWQLvtWrMEyoLkNOsw)

Without going into specifics, we can see that the values generated move between 1 and -1.

```javascript
function draw() {
  var sine = sin();
  print('Sine value: '+sine);
}
```

To move the sine wave, we can provide it with time, and to receive a smooth value we have to divide by at least 1000.

```javascript
function draw() {
  var time = millis()/1000;
  var sine = sin(time);
  print('Sine value: '+sine);
}
```

This will provide us with a smooth transition between 1 and -1, moving forward along time. However, this range is of little use controlling color, which ranges from 0-255. For that, we have to map one range to another.

## Map

To convert one range of numbers into another we use `map(value,minIn,maxIn,minOut,maxOut)` which is most often used converting a sensor input reading into a useful output, but is also useful for animations. It takes the **minimum and maximum input** and transforms into to the **minimum and maximum output.**

```javascript
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
  var a = mouseX;
  //a = constrain(a, 0, width);
  var b = map(a, 0, 400, 0, 255);
  var c = map(a, 0, 400, 255, 0);
  print(`When a is ${a}, b is ${round(b)} and c is ${round(c)}`);
}
```

![](../../../.gitbook/assets/p5-map%20%282%29.png)

```javascript
function draw() {
  var time = millis()/1000;
  var sine = sin(time);
  var mapped = map(sine,-1,1,0,255);
  print('Mapped value: '+mapped);
  background(mapped,0,0);
}
```

