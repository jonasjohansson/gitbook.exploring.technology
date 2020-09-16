# 8. Visualizing interaction

Since we are often using the mouse and keyboard to play sounds or control effect parameters, it makes to also use these as input to our visuals. This can help glue together what you hear with what you see, as well as enhance the feeling of direct feedback.

Let's draw a shape when we click the mouse. We'll use an `opacity` variable that is reset to one when we click the canvas. Then, for each draw, we'll reduce it a little to make it fade away over time.

```javascript
let opacity = 0

function setup() {
  createCanvas(window.innerWidth, window.innerHeight)
}

function draw() {
  background(255, 255, 255)
  noStroke()
  
  fill(`rgba(100, 200, 100, ${opacity})`)
  rect(0, 0, 100, 100)
  
  if (opacity > 0) {
    opacity -= 0.01
  }
}

function mouseClicked() {
  opacity = 1
}
```

{% hint style="info" %}
I'm using [template strings](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) to create the CSS `rgba()` color with opacity.
{% endhint %}

Cool, let's enhance it just a little bit by drawing it at the position where we clicked.

```javascript
let opacity = 0
let clickX = 0
let clickY = 0

function setup() {
  createCanvas(window.innerWidth, window.innerHeight)
}

function draw() {
  background(255, 255, 255)
  noStroke()
  
  fill(`rgba(100, 200, 100, ${opacity})`)
  rect(clickX, clickY, 100, 100)
  
  if (opacity > 0) {
    opacity -= 0.01
  }
}

function mouseClicked() {
  opacity = 1
  clickX = mouseX
  clickY = mouseY
}
```

