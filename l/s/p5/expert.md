# Expert



{% embed url="https://towardsdatascience.com/algorithmic-beauty-an-introduction-to-cellular-automata-f53179b3cf8f" %}

## Algorithmic Botany

{% embed url="http://algorithmicbotany.org/papers/" %}

### L-System

```markup
<script src="https://unpkg.com/p5@0.10.2/lib/p5.js"></script>
<script src="https://unpkg.com/p5@0.10.2/lib/addons/p5.sound.min.js"></script>

<script>
  // https://en.wikipedia.org/wiki/L-system
  // variables: A B
  // axiom: A
  // rules: (A->AB), (B->A)
  // axiom and rules can be modified in orther to create different trees

  var axiom = "F";
  var sentence = axiom;

  var len = 100;
  var angle;

  var hu;

  var rules = [];
  rules[0] = {
    a: "F",
    b: "FF+[+F-F+F]-[-F+F]"
  };

  // rules[1] = {
  //   a: "B",
  //   b: "A"
  // }

  function generate() {
    len *= 0.5;
    var nextSentence = "";
    for (var i = 0; i < sentence.length; i++) {
      var current = sentence.charAt(i);
      var found = false;
      for (var j = 0; j < rules.length; j++) {
        if (current == rules[j].a) {
          found = true;
          nextSentence += rules[j].b;
          break;
        }
      }
      if (!found) {
        nextSentence += current;
      }
    }
    sentence = nextSentence;
    createP(sentence);
    turtle();
  }

  function turtle() {
    background(0);
    resetMatrix();
    translate(width / 2, height);
    hu = 0;
    for (var i = 0; i < sentence.length; i++) {
      var current = sentence.charAt(i);
      stroke((hu / 10) % 256, 255, 255);
      strokeWeight(2);
      if (current == "F") {
        line(0, 0, 0, -len);
        translate(0, -len);
      } else if (current == "+") {
        rotate(angle);
      } else if (current == "-") {
        rotate(-angle);
      } else if (current == "[") {
        push();
      } else if (current == "]") {
        pop();
      }
      hu++;
    }
  }

  function setup() {
    createCanvas(400, 400);
    colorMode(HSB);
    background(0);
    angle = radians(27);
    turtle();
    createP(axiom);
    var button = createButton("Generate");
    button.mousePressed(generate);
  }
</script>

```

