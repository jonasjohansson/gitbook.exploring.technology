# Interaction

There are several [events](https://p5js.org/reference/#group-Events) that can be "listened" too; button is pressed, mouse is clicked, mobile device is shaken. Some of the events even act as a variable. Such is the case with mobile device acceleration and rotation. or framecount. Let's look at some examples how user interaction can be integrated.

## Mouse

…

## Keyboard

…

## Mobile

Due to security restrictions users must give explicit access to motion data. This is normally done by providing a button which upon being clicked prompts the user to for permission.

```javascript
let button;

function setup() {
  createCanvas(windowWidth, windowHeight);
  permission(true);
}

function draw() {
  r = map(rotationX, -90, 90, 0, 255);
  g = map(rotationY, -90, 90, 0, 255);
  b = map(rotationZ, -90, 90, 0, 255);
  background(r, g, b);
}

function permission(first = false) {
  if (first) {
    button = createButton('start');
    button.position(windowWidth / 2, windowHeight / 2);
    button.mousePressed(permission);
  } else if (typeof DeviceMotionEvent !== 'undefined' && typeof DeviceMotionEvent.requestPermission === 'function') {
    DeviceMotionEvent.requestPermission()
      .then(response => {
        if (response == 'granted') {
          button.remove();
        }
      })
      .catch(console.error);
  }
}
```

