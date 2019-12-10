# Examples

## [https://editor.p5js.org/ml5/sketches](https://editor.p5js.org/ml5/sketches)

## Video classification

{% tabs %}
{% tab title="HTML" %}
```markup
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.dom.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.sound.min.js"></script>
    <script src="https://unpkg.com/ml5@0.4.3/dist/ml5.min.js"></script>
  </head>
  <body style="padding:1rem;margin:0;font-family:sans-serif;">
    <fieldset>
      <legend>
        Train a Neural Network to distinguish between class A and class B and
        play back a sound sample for each class
      </legend>
      <div id="videoContainer" style="float:right"></div>
      <p>
        <span id="modelStatus">Loading base model...</span>
        <span id="videoStatus">Loading video...</span>
      </p>
      <div>
        <button id="ButtonA">Add A Images</button>
        <p><span id="amountOfAImages">0</span> A Images</p>
      </div>
      <div>
        <button id="ButtonB">Add B Image</button>

        <p><span id="amountOfBImages">0</span> B Images</p>
      </div>
      <p><button id="train">Train</button><span id="loss"></span></p>
      <p>
        <button id="buttonPredict">Start guessing!</button>
        <br />
        <br />
        Your custom model labeled this as: <span id="result">...</span>, with a
        confidence of <span id="confidence">...</span>.
      </p>
      <button id="save">Save</button>
      <label for="avatar">Load Model:</label>
      <input type="file" id="load" multiple />
    </fieldset>
    <script src="script.js"></script>
  </body>
</html>

```
{% endtab %}

{% tab title="JS" %}
```javascript
let featureExtractor;
let classifier;
let video;
let loss;
let imagesOfA = 0;
let imagesOfB = 0;
let classificationResult;
let confidence = 0;
let lastClass = "C";

let res = { x: 640, y: 480 };

let soundA;
let soundB;

function preload() {
  soundA = loadSound(
    "https://cdn.glitch.com/70be5f50-7f36-4c6b-b77d-8fde14e20715%2FA.mp3?v=1574764472269"
  );
  soundB = loadSound(
    "https://cdn.glitch.com/70be5f50-7f36-4c6b-b77d-8fde14e20715%2FB.mp3?v=1574764472621"
  );
}

function setup() {
  let canvas = createCanvas(res.x, res.y);
  video = createCapture(VIDEO);
  video.size(res.x, res.y);
  video.hide();
  canvas.parent(videoContainer)
  featureExtractor = ml5.featureExtractor("MobileNet", modelReady);
  const options = { numLabels: 2 }; //Specify the number of classes/labels
  classifier = featureExtractor.classification(video, options, videoReady);
  setupButtons();
}

function draw() {
  background(122);
  image(video, 0, 0);
  textSize(64);
  if (classificationResult == "A" && lastClass !== "A") {
    soundA.play();
    soundB.stop();
  } else if (classificationResult == "B" && lastClass !== "B") {
    soundB.play();
    soundA.stop();
  }
  lastClass = classificationResult;
}

function modelReady() {
  select("#modelStatus").html("Base Model (MobileNet) loaded!");
}

function videoReady() {
  select("#videoStatus").html("Video ready!");
}

function classify() {
  classifier.classify(gotResults);
}

function setupButtons() {
  let buttonA = select("#ButtonA");
  buttonA.mousePressed(function() {
    classifier.addImage("A");
    select("#amountOfAImages").html(imagesOfA++);
  });

  let buttonB = select("#ButtonB");
  buttonB.mousePressed(function() {
    classifier.addImage("B");
    select("#amountOfBImages").html(imagesOfB++);
  });

  let train = select("#train");
  train.mousePressed(function() {
    classifier.train(function(lossValue) {
      if (lossValue) {
        loss = lossValue;
        select("#loss").html("Loss: " + loss);
      } else {
        select("#loss").html("Done Training! Final Loss: " + loss);
      }
    });
  });

  let buttonPredict = select("#buttonPredict");
  buttonPredict.mousePressed(classify);

  let saveBtn = select("#save");
  saveBtn.mousePressed(function() {
    classifier.save();
  });

  let loadBtn = select("#load");
  loadBtn.changed(function() {
    classifier.load(loadBtn.elt.files, function() {
      select("#modelStatus").html("Custom Model Loaded!");
    });
  });
}

function gotResults(err, result) {
  if (err) {
    console.error(err);
  }

  select("#result").html(result[0].label);
  select("#confidence").html(nf(result[0].confidence, 0, 2));

  classificationResult = result[0].label;
  confidence = result[0].confidence;

  classify();
}
```
{% endtab %}
{% endtabs %}

## Sound Classification

{% tabs %}
{% tab title="HTML/JS" %}
```markup
<!DOCTYPE html>
<html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.dom.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.sound.min.js"></script>
    <script src="https://unpkg.com/ml5@0.4.3/dist/ml5.min.js"></script>
  </head>
  <body>
    <script>
      // Initialize a sound classifier method with SpeechCommands18w model. A callback needs to be passed.
      let classifier;
      // Options for the SpeechCommands18w model, the default probabilityThreshold is 0
      const options = { probabilityThreshold: 0.9 };
      // Two variable to hold the label and confidence of the result
      let label;
      let confidence;

      function preload() {
        // Load SpeechCommands18w sound classifier model
        classifier = ml5.soundClassifier("SpeechCommands18w", options);
      }

      function setup() {
        noCanvas();
        // Create 'label' and 'confidence' div to hold results
        label = createDiv("Label: ...");
        confidence = createDiv("Confidence: ...");
        // Classify the sound from microphone in real time
        classifier.classify(gotResult);
      }

      // A function to run when we get any errors and the results
      function gotResult(error, results) {
        // Display error in the console
        if (error) {
          console.error(error);
        }
        // The results are in an array ordered by confidence.
        console.log(results);
        // Show the first label and confidence
        label.html("Label: " + results[0].label);
        confidence.html("Confidence: " + nf(results[0].confidence, 0, 2)); // Round the confidence to 0.01
      }
    </script>
  </body>
</html>
```
{% endtab %}
{% endtabs %}

