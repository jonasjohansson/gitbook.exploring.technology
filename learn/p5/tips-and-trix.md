# Tips & Trix

## 3D

[https://p5js.org/examples/3d-geometries.html](https://p5js.org/examples/3d-geometries.html)

{% tabs %}
{% tab title="Pyramid" %}
```javascript
function setup() {
  createCanvas(400, 400, WEBGL);
}

function draw() {
  background(220);
  
  rotateX(-frameCount * 0.001);
  rotateZ(-frameCount * 0.001);
  rotateY(-frameCount * 0.001);

  var d = 100

  // 3d cone reduced into pyramid
  push();
    normalMaterial();
    cone(d,d,0,0);
  pop();
  
  // 3d pyramid made by several vertex planes
  beginShape();
    // a
    vertex(0,0,0);
    vertex(d,0,0);
    vertex(d*0.5,d,0.5);
    // b
    vertex(d,0,0);
    vertex(d,0,d);
    vertex(d*0.5,d,0.5);
    // c
    vertex(d,0,d);
    vertex(0,0,d);
    vertex(d*0.5,d,0.5);
    // d
    vertex(0,0,d);
    vertex(0,0,0);
    vertex(d*0.5,d,0.5);
    // floor
    vertex(0,0,0);
    vertex(d,0,0);
    vertex(d,0,d);
    vertex(0,0,d);
  endShape();
}
```
{% endtab %}
{% endtabs %}

## Scale trick

It's extremely tedious migrating to a responsive solution. A quick fix is to simple scale the work so that it appears responsive, but is actually just adjusted in size…

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
}

function draw() {
  background(220);
  
  responsiveScale(400); // original width

  circle(200, 200, 100);
}

function responsiveScale(w){
  var scaleRatio = (windowWidth > w) ? windowWidth / w : 1;
  scale(scaleRatio, scaleRatio);
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}
```

## Sliders



Mastering transformation will be one of many keys to making generative visuals! Try this example that uses sliders to further explain the concept of transform, rotate and push and pop:

{% embed url="https://codepen.io/mickeyvanolst/pen/mddNJqQ" %}

```javascript
function setup() {
  createCanvas(windowWidth, windowHeight);
  sliderTranslateX = createSlider(0, width, width / 2);
  sliderTranslateX.position(10, 10);

  sliderTranslateY = createSlider(0, height, height / 2);
  sliderTranslateY.position(10, 30);

  sliderRotation = createSlider(0, 360, 180);
  sliderRotation.position(10, 50);

  sliderSize = createSlider(0, width, width / 2);
  sliderSize.position(10, 70);
  
  rectMode(CENTER); // try removing this
}

function draw() {
  background(220);
  
  let tx = sliderTranslateX.value();
  let ty = sliderTranslateY.value();
  let rot = sliderRotation.value();
  let size = sliderSize.value();

  translate(tx, ty);

  rotate(radians(rot));
  rect(0, 0, size, size);
}

```

## Other



  
​[Algorithmic Beauty: An Introduction to Cellular AutomataAn overview of simple algorithms that generate complex, life-like results.towardsdatascience.com](https://towardsdatascience.com/algorithmic-beauty-an-introduction-to-cellular-automata-f53179b3cf8f)‌

## Algorithmic Botany <a id="algorithmic-botany"></a>

​[Algorithmic Botany: Publicationsalgorithmicbotany.org](http://algorithmicbotany.org/papers/)‌

### L-System <a id="l-system"></a>

exit: ⌘↩

```text
<script src="https://unpkg.com/p5@0.10.2/lib/p5.js"></script><script src="https://unpkg.com/p5@0.10.2/lib/addons/p5.sound.min.js"></script>​<script>  // https://en.wikipedia.org/wiki/L-system  // variables: A B  // axiom: A  // rules: (A->AB), (B->A)  // axiom and rules can be modified in orther to create different trees​  var axiom = "F";  var sentence = axiom;​  var len = 100;  var angle;​  var hu;​  var rules = [];  rules[0] = {    a: "F",    b: "FF+[+F-F+F]-[-F+F]"  };​  // rules[1] = {  //   a: "B",  //   b: "A"  // }​  function generate() {    len *= 0.5;    var nextSentence = "";    for (var i = 0; i < sentence.length; i++) {      var current = sentence.charAt(i);      var found = false;      for (var j = 0; j < rules.length; j++) {        if (current == rules[j].a) {          found = true;          nextSentence += rules[j].b;          break;        }      }      if (!found) {        nextSentence += current;      }    }    sentence = nextSentence;    createP(sentence);    turtle();  }​  function turtle() {    background(0);    resetMatrix();    translate(width / 2, height);    hu = 0;    for (var i = 0; i < sentence.length; i++) {      var current = sentence.charAt(i);      stroke((hu / 10) % 256, 255, 255);      strokeWeight(2);      if (current == "F") {        line(0, 0, 0, -len);        translate(0, -len);      } else if (current == "+") {        rotate(angle);      } else if (current == "-") {        rotate(-angle);      } else if (current == "[") {        push();      } else if (current == "]") {        pop();      }      hu++;    }  }​  function setup() {    createCanvas(400, 400);    colorMode(HSB);    background(0);    angle = radians(27);    turtle();    createP(axiom);    var button = createButton("Generate");    button.mousePressed(generate);  }</script>
```

