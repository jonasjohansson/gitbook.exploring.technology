# Sound Classification



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

