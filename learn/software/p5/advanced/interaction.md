# Interaction

There are several [events](https://p5js.org/reference/#group-Events) that can be "listened" too; button is pressed, mouse is clicked, mobile device is shaken. Some of the events even act as a variable. Such is the case with mobile device acceleration and rotation. or framecount. Let's look at some examples how user interaction can be integrated.

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

