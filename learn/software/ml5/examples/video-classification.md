# Video Classification

## Light and Dark

```markup
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.dom.min.js"></script>
    <script src="https://unpkg.com/ml5@0.4.3/dist/ml5.min.js"></script>
  </head>
  <body>
    <script>
      let classifier;
      let imageModelURL =
        "https://teachablemachine.withgoogle.com/models/H1sVtfEK/";

      let log, video;

      function setup() {
        noCanvas();
        log = createDiv("Loading model.");
        video = createCapture(VIDEO);
        classifier = ml5.imageClassifier(
          imageModelURL + "model.json",
          video,
          modelReady
        );
      }

      function modelReady() {
        log.html("Model loaded!");
        classifyVideo();
      }

      function classifyVideo() {
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
        classifyVideo();
      }
    </script>
  </body>
</html>
```

