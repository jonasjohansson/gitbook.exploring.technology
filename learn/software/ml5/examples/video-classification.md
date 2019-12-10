# Video Classification

## Light and Dark

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
      let modelUrl = "https://teachablemachine.withgoogle.com/models/H1sVtfEK/";
      let video, flippedVideo;

      function preload() {
        classifier = ml5.imageClassifier(modelUrl + "model.json", modelReady);
        log = createDiv("Loading model.");
      }

      function setup() {
        noCanvas();
        video = createCapture(VIDEO);
        video.size(320, 240);
        flippedVideo = ml5.flipImage(video);
      }

      function draw() {
        background(0);
        image(flippedVideo, 0, 0);
      }
      function modelReady() {
        log.html("Model loaded!");
        classifyVideo();
      }

      function classifyVideo() {
        flippedVideo = ml5.flipImage(video);
        classifier.classify(flippedVideo, gotResult);
      }

      function gotResult(error, results) {
        if (error) {
          console.error(error);
          return;
        }
        let label = results[0].label;
        let confidence = nf(results[0].confidence, 0, 2);
        log.html(`Label: ${label} <br>Confidence: ${confidence}`);
        classifyVideo();
      }
    </script>
  </body>
</html>

```
{% endtab %}
{% endtabs %}

