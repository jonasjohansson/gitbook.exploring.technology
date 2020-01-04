# PoseNet



{% tabs %}
{% tab title="Clap & Whistle" %}
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

      function preload() {
        classifier = ml5.soundClassifier(modelUrl + "model.json", modelReady);
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
        let label = results[0].label.toLowerCase();
        let confidence = results[0].confidence;
        log.html(`Label: ${label} <br>Confidence: ${confidence}`);
      }
    </script>
  </body>
</html>

```
{% endtab %}
{% endtabs %}

