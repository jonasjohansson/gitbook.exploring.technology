# Sound Classification

## Whistle and Clap

```markup
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.dom.min.js"></script>
    <script src="https://unpkg.com/ml5@0.4.3/dist/ml5.min.js"></script>
  </head>
  <body>
    <script>
      let modelUrl = "https://teachablemachine.withgoogle.com/models/gC-2OI2X/";
      let options = {
        probabilityThreshold: 0.9
      };
      let log;
      
      function preload() {
        classifier = ml5.soundClassifier(
          modelUrl + "model.json",
          modelReady,
          options
        );
        log = createDiv("Loading model.");
        //classifier = ml5.soundClassifier("SpeechCommands18w", modelReady, options);
      }

      function setup() {
        noCanvas();
      }

      function modelReady() {
        log.html("Model loaded!");
        classifier.classify(gotResult);
      }

      function gotResult(error, results) {
        if (error) {
          console.error(error);
          return;
        }
        let label = results[0].label;
        let confidence = nf(results[0].confidence, 0, 2);
        log.html(`Label: ${label} <br>Confidence: ${confidence}`);
      }
    </script>
  </body>
</html>

```

{% hint style="success" %}
The `SpeechCommands18w`  is a JavaScript module that enables recognition of spoken commands comprised of simple isolated English words from a small vocabulary. The default vocabulary includes the following words: the ten digits from "zero" to "nine", "up", "down", "left", "right", "go", "stop", "yes", "no", as well as the additional categories of "unknown word" and "background noise".
{% endhint %}

