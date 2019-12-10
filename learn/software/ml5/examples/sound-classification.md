# Sound Classification



## Whistle and Clap

This example uses the model trained above. Change the `soundModel` to your link for your input.

{% tabs %}
{% tab title="" %}
```markup
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.dom.min.js"></script>
    <script src="https://unpkg.com/ml5@0.4.3/dist/ml5.min.js"></script>
  </head>
  <body>
    <script>
      let options = {
        probabilityThreshold: 0.7
      };
      let label;
      let confidence;
      let soundModel =
        "https://teachablemachine.withgoogle.com/models/gC-2OI2X/";

      function preload() {
        //classifier = ml5.soundClassifier(soundModel + "model.json", options);
        classifier = ml5.soundClassifier(SpeechCommands18w, options);
      }

      function setup() {
        noCanvas();
        label = createDiv("Label: ...");
        confidence = createDiv("Confidence: ...");
        classifier.classify(gotResult);
      }

      function gotResult(error, results) {
        if (error) {
          console.error(error);
          return;
        }
        label.html("Label: " + results[0].label);
        confidence.html("Confidence: " + nf(results[0].confidence, 0, 2));
        timer = setTimeout(function() {
          label.html("");
          confidence.html("");
        }, 500);
      }
    </script>
  </body>
</html>

```
{% endtab %}
{% endtabs %}

